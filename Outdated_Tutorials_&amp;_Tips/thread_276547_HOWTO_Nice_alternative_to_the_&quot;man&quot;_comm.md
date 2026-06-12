---
title: "HOWTO: Nice alternative to the &quot;man&quot; command."
date: 2006-10-13
forum: Outdated Tutorials &amp; Tips
---

### Post by angrykeyboarder on 2006-10-13
[SIZE=2]There are several ways to view *man* pages in Linux.

I know you're aware of at least one way (and *probably* two if you're a Kubuntu/KDE user).

Of course the most common method is in a terminal or console:

```
$man <command>
```But for many, this is is not ideal because:[/SIZE][LIST=1]
[*][SIZE=2]They're just not used to getting help this way (e.g. coming to Linux from Windows) and/or[/SIZE]
[*][SIZE=2]Reading text in a terminal can be difficult.  This is especially true if you have poor eyesight (I fall into this category) and/or[/SIZE]
[*][SIZE=2]They would like a ***nicely*** printed version of the man page.[/SIZE][/LIST][SIZE=2]So then... **In Kubuntu:**

 You've got it made, as man pages are viewable in Konqueror by default.

Open Konqueror and type ```
#<command>
``` in the location bar. That will display the all text of the man page that you would see in a terminal, but in a much nicer [DocBook]("http://wiki.docbook.org/topic/DocBook") format.  And this utilizes your default Konqueror fonts.

So entering:

```
 #apt-get
```in Konqueror's location bar, would display the man page (right in Konqueror) for the "apt-get" command.

**In Ubuntu/Xubuntu/Edubuntu:**

The desktop users guide (the help icon) has a manual pages section.  However, it doesn't seem to have all man pages (so I almost never use it myself).

So then, we're now down to my favorite way to view man pages. And that is:

**View man pages in *****any***** web browser that you have installed.**

This is especially nice with Firefox (you'll see why later on).

There is a program that converts man pages to html on the fly. it's called (appropriately enough) [URL="http://savannah.nongnu.org/projects/man2html/"]man2html.
[/URL]
However, it *does* require that you have a web server installed (if you don't already).  If you don't, it's *very* easy to accomplish.  

There a a variety of web server programs in the Ubuntu repository.  I use the ever popular [*Apache*]("http://www.apache.org/"), but any of them should work (however, I'm not familiar with the others. I've not tried them).

For the following example, I'll use Apache.

Assuming you *don't* have a web sever installed, open a terminal and enter

[/SIZE]```
 sudo apt-get install apache2 man2html
```[SIZE=2]

(You can omit "apache2" if you *do* have it - or another- web sever installed already).

Now depending on your setup, you may have unmet dependencies, so accept whatever extra packages apt says you need to install along with the above.

When the installation(s) finish(es), take note of the last line of the response. It shows you the URL you need in order to view man pages in your browser.

Typically that URL is:

[http://localhost/cgi-bin/man/man2html](http://localhost/cgi-bin/man/man2html)

Of course you'll want to bookmark this page.

Now open that URL in your browser of choice (I recommend Firefox - read on).

On the web page you'll see a box; That's where you enter the command you'd enter if you were viewing it in a terminal (sans the "man" portion).

So, if you want a man page for the "less" command you'd simply type "less" in the box and you'd see the man page for the command.

Now this still *is* a bit cumbersome, In fact, it's faster just to view man pages the old fashioned way (in a terminal).

***However***....

This is where it gets cool, quick and easy (if you're using Firefox).

Bookmark the above URL in Firefox.

Then go to your bookmarks menu and open your bookmarks (like you would if you wanted to organize them).

Find the above bookmark.

Right click on it and select properties.

Now, you need to make two changes here.

Step 1.

In the "Location" section, append the URL with.

```
 ?query=%s
```Step 2.

Right below the location box is a keyword box.  In that box enter ```
man
```.

So in my case, all I have to do to view a man page in Firefox is to type ```
man <command>
``` in the location bar!

Therefore, typing the following in the Firefox Location bar:

```
 man aptitude
```.....would give you a web page (suitable for printing) with everything that you'd see in a terminal had you typed "man aptitude" there (but nicely formatted and with hyperlinks to related commands)!

That's it!


This may be a bit cumbersome to set up, but after you get it up and running it truly rocks (at least I think so).[/SIZE]

---

### Post by wildchild on 2006-10-13
Very nice!

---

### Post by forger on 2006-10-13
cool, i'll never close firefox again :P

---

### Post by 13east on 2006-10-13
a very nice post
this is very useful
thx

---

### Post by dagnabit dang doohickey on 2006-10-14
There's another solution for man page junkies who want to view their man pages in a web browser, but may not want to install a web server.

A man named Rolf Howarth wrote a great perl script named [manServer]("http://www.squarebox.co.uk/users/rolf/download/manServer.html") that not only parses man pages into html and works as a webserver cgi, but it also has a built-in http server so you can use it as a stand-alone script without installing a separate webserver.

I use a slightly modified version of the original. The modified version makes the commands display in a vertical list, rather than the default behavior which displays them in a cloud. You can see the difference in the two screenshots below.

If you like the default behavior you can download it from the [SEE ALSO]("http://www.squarebox.co.uk/users/rolf/download/manServer.html#12") section on the [manServer]("http://www.squarebox.co.uk/users/rolf/download/manServer.html") page.

If you prefer the vertical list behavior, You can download the attachment below.


**To install manServer:**
1. rename the script to manserver
2. copy manserver to: /usr/local/bin
3. run the following command to make it executable
```
sudo chmod +x /usr/local/bin/manserver
```

**To run manServer:**
1. Press alt+F2
2. type: manserver -s
3. click Run


To browse your local man pages go to [http://127.0.0.1:8888/](http://127.0.0.1:8888/)

To go directly to a specific command, say fstab, enter [http://127.0.0.1:8888/fstab](http://127.0.0.1:8888/fstab)

If you'd like to use angrykeyboarder's great Firefox tip, which is really what makes all of this worthwhile,
follow his instructions, but change Step 1: append the url with %s instead of ?query=%s


**If you'd like to have manServer start at bootup you can use this startup script:**
1. Name the following code manserver.sh and copy it to the /etc/init.d directory.
```
#! /bin/sh
#
#  This script was generated by The Ubuntu Linux Startup Script Builder
#  version 1.5 located at http://rob.pectol.com/startup_scriptbuilder/

PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

if [ -r /lib/lsb/init-functions ]; then
	. /lib/lsb/init-functions
	logbegin="log_begin_msg"
	logend="log_end_msg"
else
	logbegin="echo -n"
	logend=`printf "echo .\n"`
fi

# Exit if the daemon binary is NOT available, executable, etc.
test -x /usr/local/bin/manserver || exit 0

# Start function
d_start() {
	/usr/local/bin/manserver -s
}

# Stop function
d_stop() {
	the_pid=`ps -A | grep manserver | awk '{$1=$1;print}' | cut -d ' ' -f1`
	if [ "$the_pid" != "" ]; then
		kill -9 $the_pid
	else
		echo
		echo "PID not known!"
	fi
}

case "$1" in
	start)
		$logbegin "Starting manserver startup script: manserver"
		d_start
		$logend $?
		;;
	stop)
		$logbegin "Stopping manserver startup script: manserver"
		d_stop
		$logend $?
		;;
	restart)
		$0 stop
		sleep 1
		$0 start
		;;
	*)
	log_success_msg "Usage: manserver.sh {start|stop|restart}"
	exit 1
	;;
esac
exit 0
```

2. Make it executable:
```
sudo chmod +x /etc/init.d/manserver.sh
```

3. Add the symbolic links to cause the script to be executed when the system comes up, or goes down:
```
sudo update-rc.d manserver.sh defaults 99 01
```


*BTW: This startup script was created using [this fantastic online startup script generator]("http://rob.pectol.com/content/view/17/33/").*

---

### Post by DC@DR on 2006-10-14
Very useful, thanks guys for this nice HOWTO, I like it :)

---

### Post by deadlydeathcone on 2006-10-14
I stumbled upon a couple of useful things a while back:

```
yelp man:gcalctool
```

Formats any man page and displays it in Yelp, and

```
yelp info:make
```

which does the same for any info page.

I found these while researching how to make a Deskbar manpage plugin, which I'm putting off untill I learn a little more Python.

---

### Post by DonS on 2006-10-14
Regarding yelp:

You can also access man / info pages from the search entry on the toolbar:
```

man:gcalctool
man gcalctool

```
and
```

info:gcalctool

```
from the search bar will automatically bring up the correct page.

Also, the Alt-F2 dialog in GNOME allows access to man info pages using the same man:<page> or info:<page> format as the yelp command line.

---

### Post by angrykeyboarder on 2006-10-15
> **deadlydeathcone said:**
> I stumbled upon a couple of useful things a while back:

```
yelp man:gcalctool
```Formats any man page and displays it in Yelp, and

```
yelp info:make
```which does the same for any info page.

I found these while researching how to make a Deskbar manpage plugin, which I'm putting off untill I learn a little more Python.

DAYMN! ](*,)

If I'd known that this thread wouldn't exist. :-D

Thanks! :)

---

### Post by deadlydeathcone on 2006-10-19
> **angrykeyboarder said:**
> DAYMN! ](*,)

If I'd known that this thread wouldn't exist. :-D

Thanks! :)

No problem!

About that deskbar plugin... it's already been done! It's found [here]("http://eduffy.net/deskbar-plugins/index.html#man"), and it's quite nice.

---

