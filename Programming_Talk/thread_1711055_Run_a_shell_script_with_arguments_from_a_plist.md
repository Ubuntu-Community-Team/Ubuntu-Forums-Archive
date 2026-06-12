---
title: "Run a shell script with arguments from a plist?"
date: 2011-03-20
forum: Programming Talk
---

### Post by bcooperizcool on 2011-03-20
Ok, I have googled around a little bit, but never seen this question asked.
I am using an iphone 2g, and would be making something for the settings app, for theming it.

As I know next to nothing in obj-c, I made my program for themeing in bash/shell.   It currently only runs from the terminal, but I was thinking if I could run a file from a plist with arguments for its execution, I could make some form of simple GUI for it.

I would of course have to mod my script to work right and accept command line arguments, as opposed to receiving them from within the script, but thats simple.



Is this possible?  Say, how would I make a toggle/button/something to run a .sh file?

e.g. /var/mobile/sled.sh arg1 arg2


Also, it would be nice to have the arguments be set within the plist, say, have it read a folder and list the contents to be used as arguments

e.g.
Option1
Option2
Option3 (selected)
Option4

then have it run the script when the other button is pressed using the selected option as an argument

e.g. /var/mobile/sled.sh Option3 arg2


Pretty simple request, and I am thinking it has to be possible somehow, as launchdaemons can do this, just I don't know how to set the arguments for that within a plist :(


Thanks :D

---

### Post by DMaurice on 2011-04-27
bcooperizcool:
I've been looking all over for this as well. I am like 3 days old at UNIX/Mac coding, literally. I have been attempting to convert some crontab stuff while making use of launchd. Anyway, here is how I figured out to pass variables to an .sh file inside of a plist (I hard coded the location to the .sh file):

-----
<key>ProgramArguments</key>
<array>
<string>/Users/username/bin/myfile.sh</string>
<string>hourly</string>
</array>
-----

Where this is how it would look when using the crontab file previously:

30 0,3,6,9,12,15,18,22 * * * /Users/username/bin/myfile.sh hourly

My .sh file responds based on the variable that is passed to it. So rather than recoding, I can just create various plist files to run at certain times, passing the appropriate variable. This was a quick way to keep using the existing .sh file and making use of launchd and .sh files.

Of course, I need to now get the <key>StartCalendarInterval</key> to the desired settings in my plist file.

Here's the site that helped me out:
[http://guide.macports.org/chunked/reference.startupitems.html](http://guide.macports.org/chunked/reference.startupitems.html)

Hope this helps some. ciao! DMaurice

---

