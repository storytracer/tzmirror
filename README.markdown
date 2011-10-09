Mirror of the *tz* Database
===============================================

On 2011-09-30, a astrology(!) company called "Astrolabe, Inc" filed a lawsuit against the maintainers of the [time zone database](http://www.twinsun.com/tz/tz-link.htm), claiming the database infringed their copyright. The result of this lawsuit was that the [FTP server](ftp://elsie.nci.nih.gov/pub) and the [*tz* mailing list](http://news.gmane.org/gmane.comp.time.tz) were shut down at 2011-10-06.

More info about this madness is available [here](http://www.thedailyparker.com/CommentView,guid,c5f28bae-4b9c-41ea-b7b7-8891ad63c938.aspx "The Daily Parker - Time zone database shut down").

Actions like this can't be tolerated, no one can claim ownership of something as essential as timezone data. What's next? Patenting the alphabet?

Does this outrage you? You can help: Set up a mirror of the *tz* database files.

## How to set up a mirror ##

It's simple: Clone this repository to a folder on your webserver:

	$ cd /var/www/example.com/
	$ git clone --recursive https://github.com/canbuffi/tzmirror.git

Done! Your mirror should be up and running under `http://www.example.com/tzmirror/`.

## Keeping the mirror up-to-date

If your server runs Linux and has git installed, there is an easy solution to keep your mirror up-to-date:

1. Run `crontab -e` in your shell. A file editor opens up.
2. Add the following line to the end of the file:

		*	4	* * * cd /var/www/example.com/tzmirror/; /usr/bin/git fetch origin
				
	Note: ('/var/www/example.com/' has to be replaced with the actual path of the folder, where you cloned the repository into)
		
3. Save the file.

The repository is now checked for updates automatically, every night at 4 AM.

If you want to check for changes manually, you can do it by running these commands in your shell:

	$ cd /var/www/example.com/tzmirror/
	$ git fetch origin

## List of Known Mirrors

After you have set up your mirror, please add the URL to the list of known mirrors in the [wiki](https://github.com/canbuffi/tzmirror/wiki).

## *tz* database files

A tiny detail: This repository contains the files and directory structure for setting up a mirror. The actual *tz* database files are hosted outside of the US, on gitorious.org, rather than on github.com. However, they are linked to this repository as a submodule and get downloaded automatically as you clone it.

## LICENSE

The *tz* database files are public domain, as well as the mirror website files. Mirroring, forking and contributing is encouraged. Let's give them a taste of the good old [Streisand effect](http://en.wikipedia.org/wiki/Streisand_effect "Streisand effect - Wikipedia, the free encyclopedia").