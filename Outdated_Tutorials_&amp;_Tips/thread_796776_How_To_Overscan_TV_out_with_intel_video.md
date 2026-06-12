---
title: "How To: Overscan TV out with intel video"
date: 2008-05-16
forum: Outdated Tutorials &amp; Tips
---

### Post by gcpete on 2008-05-16
So TV out is working on your laptop with integrated intel video card but the picture does not fill the screen, very annoying when your trying to watch movies. The problem is caused by a lack of overscan. This can be corrected fairly easily using a simple command line tool. No permanent changes to your X configuration are made so it has to be run each time you want to correct your TV picture, details of how to do this are also included

1) Download and compile: [http://wilmer.gaast.net/blog/archives/34-Change-Intel-X.org-TV-Out-margins.html]("http://wilmer.gaast.net/blog/archives/34-Change-Intel-X.org-TV-Out-margins.html"). 

Or

1A) If you don't feel like that use the deb attached to this post which works on 7.10 and 8.04. 
Download and double click to install. 


2) Connect your TV and activate the output, eg with a button combo or xrandr command (I guess you can get the picture on the TV or you would not know you had annoying black lines!

Now open up a terminal (Applications -> Accessories -> Terminal) and enter

```
xtvmargin TOP -set 17
xrandr --output TV --mode 640x480
xrandr --output TV --mode 1024x768
```

The last to are needed to activate the changes you made. Now look at the TV picture and see how close to the top the menu is, repeat the process adjusting the value until you find a position you like. 

3) Now repeat the process for TOP BOTTOM LEFT RIGHT.

For the record my values are

```
xtvmargin TOP -set 22
xtvmargin BOTTOM -set 40
xtvmargin LEFT -set 20
xtvmargin RIGHT -set 15
```

Once you have found values that work make a small script to allow you to configure the TV output easily. 

4) Copy and paste the following into a new file, substituting the values given for the ones you found above.



```
xtvmargin TOP -set 22
xtvmargin BOTTOM -set 40
xtvmargin LEFT -set 20
xtvmargin RIGHT -set 15
xrandr --output TV --mode 640x480
xrandr --output TV --mode 1024x768
```


Save the file with a name that makes sense to you I use tv. 

5) Now using nautilus right click on the files icon select properties then the permissions tab and tick the allow file to be executed box. Close the properties window.

6) Now double click on the file you just created, select run in terminal and hey presto your done. 

(Optional)
You could if you want now copy this file to the /usr/local/bin directory to allow everyone who uses the system to access it. If you do that you will probably also want to add a menu entry for it using the System -> preferences -> main menu tool, don't forget to select run in terminal when you create the menu entry.

Works for me and only takes about ten mins from start to finish to set up.

peter

---

### Post by kaoskorruption on 2010-05-29
Problem:

> chris@Wolf:~/Desktop/xtvmargin$ ./xtvmargin TOP -set 17
No outputs have `TOP' property

> chris@Wolf:~/Desktop/xtvmargin$ xrandr --output TV --mode 1440x900
warning: output TV not found; ignoring

My output is not TV, but rather HDMI2, but this still doesn't work:

> chris@Wolf:~/Desktop/xtvmargin$ ./xtvmargin TOP -set 22 -display HDMI2
Cannot open display "HDMI2"

---

### Post by mprice2010 on 2010-06-26
Hi Guys

i was having the same error as [kaoskorruption]("http://ubuntuforums.org/member.php?u=411697") "No outputs have `TOP' property" if you type 

```


xrandr --prop


```look throught the output for the display you want to overscan. There will be a section like this:

    bottom margin: 37 (0x00000025)    range:  (0,100)
    right margin: 46 (0x0000002e)    range:  (0,100)
    top margin: 36 (0x00000024)    range:  (0,100)
    left margin: 54 (0x00000036)    range:  (0,100)
 

These are your parameters. So then you type:

```


./xtvmargin "top margin" -set -22


```These parameters may be different for you

Hope this helps.

---

