---
title: "HOWTO: Get a useful text-based desktop (embedded terminal plus conky)"
date: 2008-02-27
forum: Outdated Tutorials &amp; Tips
---

### Post by chochem on 2008-02-27
This howto will explain how to go about turning your desktop into a useful text-based interface with input (an embedded terminal always on top the desktop of every workspace) and output (simple, useful and unobtrusive alerts about unread mail, music playing, downloads finished etc.). Using the desktop as a text interface is convenient, unobtrusive and has a nice retro-tiling-window-manager charm :)

Some of this ground is covered in other howtos. Apart from gathering the information and adding new bits, this will focus on being fairly minimalist (in keeping with the overall theme), using lightweight, single-purpose apps. No Compiz-Fusion required.

Please note: Especially the conky part of this howto supposes a modicum of familiarity with shell scripts, i.e. knowing what a 'shell script' is, what file permissions are (and how to change them), and how to execute scripts (by using and modifying the $PATH variable or writing out the absolute path of the script). If all this is completely foreign to you, you might want to reconsider if this is for you, or if you're interested in learning, check out this excellent [tutorial]("http://www.linuxcommand.org/wss0010.php") at linuxcommand.org. Ten minutes well spent, I promise.

[IMG]http://pics.viharpander.dk/posts/textdesk.png[/IMG]

[SIZE="2"]**Embedded terminal**[/SIZE]
This will use the XFCE4 terminal (GNOME users can install - sudo apt-get install xfce4-terminal - it is fairly lightweight - or check out [this thread]("http://ubuntuforums.org/showthread.php?t=202249"))

Most of the necessary settings to run the native xfce4 terminal as an 'embedded' terminal (i.e. dropping borders and bars and stuff) can be set at the command line when running it. Some can't, so enter the terminal preferences ( Edit | Preferences ) and disable scrollbars in the General section (Scrollbar is: disabled). In the Appearance section, choose 'Transparent backround' and turn the shade slider down to none. These settings will also affect 'normal' terminals (as long as you use xfce4-terminal for 'normal' sessions) but it will not render it unusable, just a little odd. 

Now when we run the terminal with the command line:
```
xfce4-terminal --hide-menubar --hide-borders --hide-toolbars
```we'll have a free-floating terminal.

However, we still need for the terminal a) to occupy a specfic portion of the screen, b) appear below all other windows on every workspace and c) not appear in the tasklist or the pager (the one showing a small representation of your workspaces) in order to properly call it embedded. For this we'll use a little tool called wmctrl (devilspie as recommended by some other howtos is pretty cumbersome, needs to be loaded beforehand and has horrible documentation). wmctrl will identify your new terminal window and add all the abovementioned qualities to it. Install wmctrl:
```
sudo apt-get install wmctrl
```Here I've put it all in a small script that starts the terminal and adjusts it in one fell swoop (if you're unfamiliar with the syntax, the &&'s wait for the former command to exit succesfully before starting the next command):

```
#! /bin/bash

xfce4-terminal --hide-menubar --hide-borders --hide-toolbars --title=descon && wmctrl -r descon -e 0,10,10,720,720 && wmctrl -r descon -b add,sticky,below && wmctrl -r descon -b add,skip_pager,skip_taskbar
```First xfce4-terminal starts a stripped terminal with the title *descon*. wmctrl then runs with various arguments: "-r descon" identifies the window, we've just named, to be targeted. The "-e [numbers]" is the geometry bit, i.e. where should the window be placed and how big should it be. 0 is for 'gravity' (can be disregarded for the purposes of this howto - just leave it at 0). 10,10 is for upper left corner coordinates, i.e. how far from the top left corner of the screen should the top left corner of the window be. 720,720 is for the width and height of the window (in that order). "-b [action],[property]" tells wmctrl to change the specified properties of the window targeted. In this case we tell it to add the sticky quality (reappering on all workspaces), and the below quality (stays below other windows even when focused), and tell it not to show up in the pager (showing workspaces) or the taskbar. If you want to know more about wmctrl and what it can do, it has a very good MAN page (type 'man wmctrl' at the command line).

Edit the script above to your liking, e.g. change the size of the window to fit your screen and your taste. Save it, e.g. in a 'scripts' directory in your home directory, and make it executable ( chmod a+x [name of script] ). 

Test that it works by starting a "Run program" window (Alt+F2 on most systems) and enter the following command:
```
xfce4-terminal -x [location and name of script, e.g. /usr/local/bin/descon]
```(Note: we run a shortlived terminal which fires off our script - dont't ask why, this just appears to be necessary)
After a short flickering you should have a terminal on your desktop.

Now, we're going to add it to 'Autostarted applications' (XFCE-specific; GNOME users: it's probably something with autostart, sessions or startup). Click Add, type in a name and a description and enter "xfce4-terminal -x [location and name of script]" in the 'Command:' line. Click 'Ok' and close the Autostarted applications (making sure that your new app is ticked).

Please note that if you're using session saving (this has only been tested on XFCE4 but I assume that it applies to any kind of session saving) that you should NOT save a session with the embedded terminal running as the saved session info does not include the properties that wmctrl adds to the window, i.e. below, skip_pager, etc.

[SIZE="2"]**Text-alerts**[/SIZE]
I tend to keep the terminal in the left hand side of the desktop, reserving the right hand side for these handy little notifications. As opposed to popups and the like, these do not make a big noise and a splash but will be easily decipherable when you (happen to) glance at the desktop. They can probably also replace a panel or a half.

We'll be using Conky for this. It's intended as a geek toy with more system info and tiny graphs  than even administrators will ever need. It does however also allow you to run your own scripts and print the output to the desktop. Note that since some of the scripts, I supply, assume you to be using a specific program (for mail, music etc.), they may be more relevant to you as inspiration for your own scripts. Feel free to write back if you need help setting it up.

Install conky:
```
sudo apt-get install conky
```Conky is configured by way of a single file in your home directory, .conkyrc. To get a customized one, try the one attached to the thread and rename it.

The .conkyrc file is divided into two: First comes global options, then a line saying 'TEXT' and then follows what you want it to display. Most global options are self-explanatory. Notice that we've got lines saying
```
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
... and further down:
alignment top_right
gap_x 10
gap_y 10

```which gives the conky window the same qualities as our terminal, so we'll not need to use wmctrl here (gap is the distance of the window to the corner set in alignment). Make sure to match the colour and font to the ones you use in your terminal for best effect.

```
TEXT
${alignr}${time %A %d %B} ${time %k:%M}
${alignr}${texeci 60 con_acpi}
${alignr}${texeci 10 con_mpc}
${alignr}${texeci 60 con_mail0}
${alignr}${texeci 60 con_mail1}
${alignr}${texeci 60 con_mail2}
${alignr}${texeci 60 con_torrent}
${alignr}${texeci 60 con_notes}

```As for text, conky reads one line at a time, so each line here is right aligned (by preceding the desired output with ${alignr} ). ${time %A %d %B} is a conky function that outputs the current weekday and date and ${time %k:%M} outputs the current time in hours and minutes. The ${texeci [interval] [script name]} lines each causes conky to run a script at the set interval and print the output. Please note that according to the conky web site this should be somewhat more taxing on the system than using conky functions - I haven't noticed any performance drain whatsoever (I'm on a 1.7 GHz 1Gb RAM system - adjust expectations according to your specs).

You can add quite a lot of functionality to conky by using the inbuilt functions (see: [http://conky.sourceforge.net/](http://conky.sourceforge.net/) and the thread [http://ubuntuforums.org/showthread.php?t=205865](http://ubuntuforums.org/showthread.php?t=205865) for more info). My point is to get something else out of it. Here's a few scripts that I've got it running. Copy/modify them if they're useful to you (and be sure to a) make them executable, b) add them to a directory covered by your path variable or use the absolute location). 

**Unread mail (Thunderbird/mbox)**
```
#! /bin/sh

unreadmailcount=$(grep -c "X-Mozilla-Status: 0000" [path to your inbox])
if [ $unreadmailcount -ge 1 ]; then 
    echo "You have $unreadmailcount unread mail in [ insert name of email account ]"
fi

```This will scan your Thunderbird inbox file for the line "X-Mozilla-Status: 0000" which signifies an unread email and delivers the line count to be read out as "You have x unread mail in [email]whateveryour@mailaddress.is[/email]" Conky supposedly has an mbox scanner but I havent't been able to get it to work.

**Notes**
This is a simple note taker that makes use fo the fact that we now always have a terminal at hand. Simply type 'cnote [content of note]', hit enter, and it'll appear shortly on your desktop courtesy of conky. To get rid of a note again, just type 'cnote rm [a single word or phrase appearing in the note, e.g. 'milk' to delete 'remember the milk!']. It doesn't get any easier.

The 'cnote' script (the one we use to take down the note):
```

#! /bin/bash

if [ "$1" = "rm" ]; then
	notekeyword="$2"
	for i in $(ls /home/user1/.notes/); do 
		notecontent=$(cat "/home/user1/.notes/${i}")
		if [[ "$notecontent" =~ "$notekeyword" ]]; then
			echo "Deleting \"$notecontent\"..."
			rm "/home/user1/.notes/${i}"
		fi
	done
else
	echo "$*" > /home/user1/.notes/note${RANDOM} && echo "Note saved"
fi

```
Replace '/home/user1/.notes/' with wherever you wish to save your notes (and be sure to create the directory) and save the script (the example above uses the name 'cnote' but use whatever name you see fit). We need to make a short script for conky that will let it read out all the note files we have saved in the note directory:
```

#! /bin/bash

for i in $(ls /home/user1/.notes); do
	cat "/home/user1/.notes/${i}"
done

```
Again: substitute and save.

**Torrents**
This is really simple. Most torrent clients have the option to move a finished torrent to a specific directory. This script simply scans that directory and reports any finds. 

```
#! /bin/sh

listcount=$(ls [path to completed torrents] | grep -c .)
if [ $listcount -eq 1 ]; then
    echo -n "\"$(ls [path to completed torrents])\" has finished downloading";
fi
if [ $listcount -gt 1 ]; then
    echo "The following torrents have finished downloading:"
    ls [path to completed torrents]
fi
```

**Music playing**
This is specific to the [Music Playing Daemon]("http://www.musicpd.org/"), or MPD, and the client MPC. It simple formats the status output of MPC to produce a simple line displaying what song is currently playing.

```
#! /bin/sh
mpcplaying=$(mpc status | grep -m 1 .)
title=$(echo $mpcplaying | sed -e 's/^[^[^\-]*\ \-\ //g')
artist=$(echo $mpcplaying | sed -e 's/\ \-\ .*$//g')
if [ "$artist" != "$title" ]; then
    echo "MPD is playing \"${title}\" by ${artist}"
fi

```**Battery**
This shows battery power in percentage when running on battery power.
```
#! /bin/sh

percentage=$(acpi | grep discharging | grep -o -E [0-9]+%)
if [ -n "$percentage" ]; then
    echo "The battery has $percentage left"
fi
```

As some hardcore conkyheads may have noticed some of these duplicate built-in functions. The difference is that since we don't want tons of lines of text, these only display if there actually is something to report, otherwise you just get a blank line. 

Hope this has proved useful or provided some inspiration :)

---

### Post by Nythain on 2008-02-29
Great howto... i was completely unaware of wmctrl, and if its even an inkling better than devilspie (wich i cant get to work 90% of the time) then, im sold.

a note on the conky usage of scripts vs. built in functions... the newest<?> version of conky has built in if/then capabilities, meaning if mpd is running then it will perform said action, if not, it moves on to the next bit... wich in turn, could lighten the load of scripts run...

also, while its true on most really modern machines, runninng scripts vs built in functions and on a frequent interval wont produce much if any difference in performance, on older and really old machines, an extra script or two is the difference in a few percent of cpu power...

i would imagine, if the scripts were running at different intervals, and you arent having conky do much as far as built in features on a 1.0 second interval (ie cpu graphs, memory graphs, disk space bars and up/download speeds) then actually running multiple scripts instead of built in features could theoretically result in less cpu usage on a more average scale...

but im not that smart, so im probably wrong... either way, thanks for the howto, very informative, even for a more "seasoned" ubuntu user

---

### Post by chochem on 2008-03-01
Thanks, Nythain :)

> a note on the conky usage of scripts vs. built in functions... the newest<?> version of conky has built in if/then capabilities, meaning if mpd is running then it will perform said action, if not, it moves on to the next bit... wich in turn, could lighten the load of scripts run...

I noticed this one and tried it but maybe I didn't play around with enough. My problem is that 'if MPD is running' is sort of a dead end: AFAIK on my system it's always there, It's a daemon, I take it that that's what it's supposed to, right? Whether or not it's doing anything is another matter alltogether. IIRC the MPD part always displayed - it just showed that no music was playing. But as I said, maybe I got it wrong?

> also, while its true on most really modern machines, runninng scripts vs built in functions and on a frequent interval wont produce much if any difference in performance, on older and really old machines, an extra script or two is the difference in a few percent of cpu power...

You're right, of course. I should probably have added some specs so people could estimate whether it was worth it on their own machine. I sort of have a feeling that this way of doing things is 'wrong' but until I know hot to to program C, I'll probably stick with scripting :)

Thanks again for the praise.

[QUOTE=dustin]in this how-to, i use my top left corner for icons. how would i possibly change this to the bottom left or top right? i've been fooling around and wmctrl doesnt like my coordinates much at all.[/QUOTE]

Hi Dustin and welcome to the forums,
Uhm I should probably recommend that you use forum posting rather than PMing since other people might profit from Q&As. That said: I suppose you're referring to the terminal part. I'm not sure that I can explain it any better than I did in the howto, unless you give me more specific info. AFAIK wmctrl only takes coordinates from the top left corner (i.e. you can't make it relative to e.g. the bottom right corner, like I believe devilspie can). So you should take note of your screen resolution and do a bit of arithmetic to figure out how far down and to the right, you'll need to push the window. As for entering coordinates, here's what the wmctrl MAN page has to say on the subject:

> A move and  resize  argument  has  the  format  &#8217;g,x,y,w,h&#8217;.   All  five
components  are  integers.  The  first  value,  g, is the gravity of the
wndow, with 0 being the most common value (the default  value  for  the
window). Please see the EWMH specification for other values.

The  four remaining values are a standard geometry specification: x,y is
the position of the top left corner of the window, and w,h is the  width
and height of the window, with the exception that the value of -1 in any
position is interpreted to mean that the current geometry  value  should
not be modified.


---

### Post by PinkFloyd102489 on 2008-03-01
What do I do with the mail script to get Conky to run it?

---

### Post by chochem on 2008-03-02
> **PinkFloyd102489 said:**
> What do I do with the mail script to get Conky to run it?

First of all, you need to be permitted to execute it. You add permissions with the command 'chmod'. 
```
chmod a+x [location and name of script, e.g. /home/user1/.myscripts/conky_mail] 
```will allow everybody to execute it

Now, conky has to be able to find the script, so either you add the current location to your $PATH (a variable containing all the places the shell looks for programs), sudo copy the script to a directory already contained in $PATH (/usr/local/bin is a popular choice) or just type out the entire location of the script on the texeci line (recommended as you're not going to be using the script yourself, only conky needs access to it), e.g.
```
${alignr}${texeci 60 /home/user1/.myscripts/conky_mail}
```
If it's still not producing output, do the ususal checks: run it yourself (just use the same line as above, i.e. '/home/user1/.myscripts/conky_mail') and see if there's any output, check that you're pointing to your Inbox file (it is called 'Inbox') and that you've actually got unread mail in it.

Hope that helps.

---

### Post by JT9161 on 2008-03-02
Thanks for the howto but both the terminal and conky get minimized when I use hide all windows and after awhile the disaper from the desktop all together even though the process are still there any one know hot to fix that

---

### Post by chochem on 2008-03-02
If by 'hide all windows' you mean the 'show desktop' function, I can only get that to apply to the terminal/conky if I emove the 'skip_taskbar' property (supposedly the function looks in the taskbar and minimizes all the windows there). Try doing 'wmctrl -r descon -b add,skip_taskbar' and see if it still minimizes. Otherwise it might be a window manager/desktop environment thing - I tried running it in Openbox and not all properties seemed to work.

---

### Post by Puptentacle on 2008-05-06
Hey, this is great and is the only version of a how to for this that actually works. wmctrl is AWESOME! 

I'm having a little problem, however. I've changed the script to try and put the terminal at the upper left corner of my desktop but it's insisting on sitting nearly dead center. No changes to the script seem to have any effect. Any clue what I can do to fix this? I'm using an HP laptop with a Centrino Duo 1.6ghz, hardy and it's all up to date. Thanks!

---

### Post by agim on 2008-05-06
This is a spectacular concept. I am working on a couple of other things right now, but I am definitely going to check this out.

---

### Post by chochem on 2008-05-07
> **Puptentacle said:**
> Hey, this is great and is the only version of a how to for this that actually works. wmctrl is AWESOME! 

I'm having a little problem, however. I've changed the script to try and put the terminal at the upper left corner of my desktop but it's insisting on sitting nearly dead center. No changes to the script seem to have any effect. Any clue what I can do to fix this? I'm using an HP laptop with a Centrino Duo 1.6ghz, hardy and it's all up to date. Thanks!

Two things come to mind: The first is that putting starting windows at the center of the screen might be the default for your window manager and somehow wmctrl is unable to change that - although this sounds implausible. The second is the possibility that wmctrl fires too early to move the window - something that I myself have seen before. What about the other attributes? Does it appear on every desktop and not in the pager or taskbar etc.? 

If none of it is sticking, try running the parts of the chain by themselves, i.e. first start the terminal, then run th first wmctrl command, then the second etc. If it works this way round, you might have to stick some sleep commands in between each stage to give the system time to catch it's breath.

If it is only the positioning that's giving you trouble you could use xfce4-terminal's own geometry setting. I didn't originally suggest this because I hadn't understood that when setting width and height this way you were tellling it how many rows and columns of *monospace character spaces* you wanted, not pixels. Try deleting the wmctrl bit about geometry ("&& wmctrl -r descon -e 0,10,10,720,720") and starting xfce4-terminal with this additional parameter: "--geometry=[width]x[height]+[distance from left edge of screen]+[distance from top of screen]" And remember that width and height are in columns and rows, respectively. 

On a final note, I have to admit that I'm no longer using this method myself. I felt that my XFCE setup was too GNOME-ish and decided to start from scratch with another window manager, called Openbox. I liked the simplicity of it and as a little bonus I found out that you can setup Openbox to do all the things that wmctrl does in this method by default - i.e. like devilspie, but much simpler and more reliably. I can recommend it for anybody who likes configuring and tweaking and who doesn't mind square corners ;) I'll include links to two excellent blogs which feature a lot of Openbox tips: 

urukrama's openbox guide:
[http://urukrama.wordpress.com/openbox-guide/](http://urukrama.wordpress.com/openbox-guide/)

and of course kmandla's:
[http://kmandla.wordpress.com/software/](http://kmandla.wordpress.com/software/)

with a little hyperbole-but-true quote from the latter ;)
> For my money there&#8217;s nothing faster or better than Openbox. My life changed for the better when I stopped relying on Gnome and all its immensity to do the simple task of interacting with me. And I learned a lot more too, when I stopped using it. If you want to understand Linux and get to know it up close and personal, find a window manager that makes you learn. Openbox will do that.

---

### Post by Puptentacle on 2008-05-13
Sorry, just getting back to this. I think I'm going to give Openbox a try as well. Looks interesting. Thanks for the thoughtful reply.

---

### Post by chochem on 2008-05-13
Cool. I should just add that the Openbox method I was referring to, is done by adding an <application></application> entry to the main Openbox configuration file, ~/.config/opebox/rc.xml between the <applications></applications> tags (at the very bottom of the file). You can add some criterion for matching, e.g. name, and what the window manager should do with a match. Here's the commented out explanation from the standard rc.xml file itself to give people a sense of the possibilities:

```
    <!--
  # this is an example with comments through out. use these to make your
  # own rules, but without the comments of course.

  <application name="first element of window's WM_CLASS property (see xprop)"
              class="second element of window's WM_CLASS property (see xprop)"
               role="the window's WM_WINDOW_ROLE property (see xprop)">
  # the name or the class can be set, or both. this is used to match
  # windows when they appear. role can optionally be set as well, to
  # further restrict your matches.

  # the name, class, and role use simple wildcard matching such as those
  # used by a shell. you can use * to match any characters and ? to match
  # any single character.

  # when multiple rules match a window, they will all be applied, in the
  # order that they appear in this list


    # each element can be left out or set to 'default' to specify to not 
    # change that attribute of the window

    <decor>yes</decor>
    # enable or disable window decorations

    <shade>no</shade>
    # make the window shaded when it appears, or not

    <position>
      # the position is only used if both an x and y coordinate are provided
      # (and not set to 'default')
      <x>center</x>
      # a number like 50, or 'center' to center on screen. use a negative number
      # to start from the right (or bottom for <y>), ie -50 is 50 pixels from the
      # right edge (or bottom).
      <y>200</y>
      <monitor>1</monitor>
      # specifies the monitor in a xinerama setup.
      # 1 is the first head, or 'mouse' for wherever the mouse is
    </position>

    <focus>yes</focus>
    # if the window should try be given focus when it appears. if this is set
    # to yes it doesn't guarantee the window will be given focus. some
    # restrictions may apply, but Openbox will try to

    <desktop>1</desktop>
    # 1 is the first desktop, 'all' for all desktops

    <layer>normal</layer>
    # 'above', 'normal', or 'below'

    <iconic>no</iconic>
    # make the window iconified when it appears, or not

    <skip_pager>no</skip_pager>
    # asks to not be shown in pagers

    <skip_taskbar>no</skip_taskbar>
    # asks to not be shown in taskbars. window cycling actions will also
    # skip past such windows

    <fullscreen>yes</fullscreen>
    # make the window in fullscreen mode when it appears

    <maximized>true</maximized>
    # 'Horizontal', 'Vertical' or boolean (yes/no)
  </application>

  # end of the example
-->

```

---

### Post by Alucard-sama on 2008-05-15
K I did everything this tutorial said, but when I use [Alt+F2] to run it -and therefore also by autostart running it- it overlaps conky AND it appears in GNOME Panel.

---

### Post by jjgomera on 2008-06-01
Hello

I've used this howto with gnome, and i have problems, wmctrl doesn't do nothing, with script or with individual command, doesn't do nothing

Have anybody success with this howto in gnome, or only in xfce or any other wm?

---

### Post by Bionic_Beefpile on 2008-07-31
wmctrl works fine for me (gnome using OpenBox as window manager) as long as I run the xfce4-terminal -x [script] command after startup.  During startup, I get the transparent window, but it never "embeds" itself.  If I try adding sleep X && [command] in the gnome session entry, the terminal never shows up at all.

---

### Post by Niedra on 2008-08-06
What does this mean ?
```
Script started, file is typescript

```
I can't get that script to work. Saved it even like mentioned in example.

---

### Post by Xavier Oddmon on 2008-08-07
Just a suggestion. Instead of using wmctrl to position the conky window, compiz-fusion has a window rules function built in that does this for you.

[EDIT]
That may actually be compiz-git.

---

### Post by Pirate_Hunter on 2008-08-07
hi this is interesting i ahve tried this on my ubuntu netwrok install with icewm installed however the terminal only shows on the first desktop and not the others, where am i going wrong or could it be my windows manager "which i find it unlikely".

---

### Post by RATM_Owns on 2008-08-07
I can't get it to work on my desktop.
As in, I can't find out how to get it to cover the desktop.

I have a 1440x900 screen so if I'd cut off the top menu that's  like maybe 1440x880?

Because here's the file:

[FONT=monospace]#! /bin/bash

xfce4-terminal --hide-menubar --hide-borders --hide-toolbars 
--title=descon && wmctrl -r descon -e 0,10,10,1440,880 && wmctrl -r 
descon -b add,sticky,below && wmctrl -r descon -b 
add,skip_pager,skip_taskbar

And it's not working. So um...help?
[/FONT]

---

### Post by mcbean on 2008-08-17
First of all, thanks! It's been very fun messing around with this. I had no idea about conky. 

I was wondering if anyone could tell me how you could check for completed torrents if you're using Transmission? I don't seem to be able to have the file moved when it's completed, so the script you provided wouldn't do anything ^^.

---

### Post by gbear14275 on 2008-12-29
I have also been trying to get the embedded terminal and scripting to work with GNOME as well.  Running close to a default install of 7.10.  Being a bit of a linux beginner though it has taken me quite a bit of time trying to figure out how to get the script running correctly.  I have been lucky to have the help of a few gracious persons on IRC who have helped to modify the commands some.  Here is where I am at (I renamed the xfce-terminal window):

Running this from the terminal works (with the exception of sticky which I have been unable to get working)

```
xfce4-terminal --hide-menubar --hide-borders --hide-toolbars --title=dskterm & sleep 1 && wmctrl -r dskterm -e 0,10,10,720,720 && wmctrl -r dskterm -b add,sticky,below && wmctrl -r dskterm -b add,skip_pager,skip_taskbar
```

I have not been able to get the script to execute but that may be a lack of my knowledge of how to get write or execute scripts.  Here is the header I am adding and I am naming the file "desktopterminal.sh".

```
#!/bin/bash

xfce4-terminal --hide-menubar --hide-borders --hide-toolbars --title=dskterm & sleep 1 && wmctrl -r dskterm -e 0,10,10,720,720 && wmctrl -r dskterm -b add,sticky,below && wmctrl -r dskterm -b add,skip_pager,skip_taskbar
```

I am still trying to work through getting the sticky command of wmctrl to work I get this output when running the command with the verbose tag:

```
$ wmctrl -r dskterm -b add,sticky -v
envir_utf8: 1
Using window: 0x03c0000a
State 1: _NET_WM_STATE_STICKY

```

Again I apologize if this is useless, am learning as I go but... if anyone is out there that might find this useful or might have a tip or two... would be very grateful.  Thanks.

---

### Post by chalewa on 2008-12-29
anyone have any screen shots of this?

---

### Post by gbear14275 on 2008-12-29
I'm hoping for something like this: 
[http://www.tashazo.com/wp-content/uploads/2007/02/conkyscreenshot512x384.png](http://www.tashazo.com/wp-content/uploads/2007/02/conkyscreenshot512x384.png)

I really like the look of the transparent system status and terminal inputs.

That reminded me though of the other problem I am having.  Even though I am able to put the terminal window "below" everything else... it still covers up icons... anyway to fix this?

---

### Post by gbear14275 on 2008-12-31
been looking (unsuccessfully) for details about the "sticky" and "below" options of wmctrl that seem to not be working.  Anyone know where I can find out more?

Thanks
Garrett

---

### Post by Caleb.Robertson on 2010-06-25
I know this post is over a year old but I was tying to make this work with Ubuntu 8.10 and 9.10. I have followed this tutorial to the letter and can't seem to get it to work. Any help would be much appreciated.


Nevermind I got it a different way 
[http://ubuntuforums.org/showthread.php?t=202249&highlight=terminal+desktop](http://ubuntuforums.org/showthread.php?t=202249&highlight=terminal+desktop)

---

