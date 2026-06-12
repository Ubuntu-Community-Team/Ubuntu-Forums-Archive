---
title: "[SOLVED] Creating a file through terminal"
date: 2008-08-31
forum: New to Ubuntu
---

### Post by Clippy on 2008-08-31
Hello!

I am a complete newbie (long-time Windows user, just started using Ubuntu Hardy last week), and I am trying to solve an issue related to losing sound after waking the computer from Suspend.  I think I have found the solution over on [this thread]("http://ubuntuforums.org/showthread.php?t=209740&page=2") (see post no. 18 ), but I'm not entirely sure how to implement it.  I have searched the net (and these forums specifically) for several hours to try to find out how to do this, but I'm still confused: I think it's time to ask for help! :rolleyes: 

Here's where I'm at:

I opened the terminal and navigated to ```
~ /etc/pm/sleep.d/
``` 
From [this site]("http://fak3r.com/2008/02/25/howto-sound-after-hibernate-in-linux-gustylenny/") I figured out (?) that entering ```
vi /etc/pm/sleep.d49sound
``` would allow me to create the necessary file (though I don't know if this is the "right" way to do it).  Once I did that, I pasted the following code (copied from the original solution thread) into the terminal window:

```
function kill_sound_apps() {
pidsnd=$(lsof | grep /dev/snd | awk '{ print $2 }')
pidmixer=$(lsof | grep /dev/mixer | awk '{ print $2 }')
piddsp=$(lsof | grep /dev/dsp | awk '{ print $2 }')
kill $pidsnd $pidmixer $piddsp
}

case "$1" in
hibernate|suspend)
kill_sound_apps
echo `date` shut down sound for pm
;;
thaw|resume)
modprobe -r snd_hda_intel
modprobe snd_hda_intel
echo `date` starting sound coming out of pm
;;
*)
;;
esac

exit $?
```
This is where I'm getting really lost (okay, so I was lost a long way back, but anyway).  I can't figure out how to save the code I just pasted.  Anything I do seems to brings up capital letters that don't mean much to me, e.g.:

```

A
B
B
A

C
```
Worse, when I closed terminal and tried to go through the process again, I was told that apparently whatever I had input on the previous attempt was saved in the swap (as d49sound.swp I believe) and thus I should proceed with caution (I tried to copy the message, but once I clicked on it it disappeared and went to a new screen that I think was the same one I pasted the code into earlier but couldn't save).  

Anyway, it's probably abundantly clear by now to you that I have no idea what the heck I'm doing. :)  For all I know I'm going about this completely wrong.  If anyone would be so kind as to walk me through this (ideally in fairly simple terminology, if possible), I would truly appreciate it.  

Thanks!

---

### Post by halitech on 2008-08-31
try this from the terminal
```
sudo touch /etc/pm/sleep.d49sound
```
then ```
gksu gedit /etc/pm/sleep.d49sound
```
this will create the file and then allow you to open the file as root so you can add the info and save it

---

### Post by Catalyst2Death on 2008-08-31
Vi is a nasty editor for newbies, so I would suggest using gedit or nano to do what you want:

```
$ sudo nano /etc/pm/sleep.d49sound
```

(paste in what you want)

Ctrl+X answer yes to (over-)write file and hit enter. Your done!

```
$ gksudo gedit /etc/pm/sleep.d49sound
```

Paste in (Ctrl+V) and save (Ctrl+S) close, and Your done!

Note:  You need the "sudo" command to ensure that you have root permissions when you open the file this way you can write your changes to disk.  gksudo is the command that corresponds to GUI programs to be ran as root.

If you're interested in using vi: [http://acs.ucsd.edu/info/vi_tutorial.shtml](http://acs.ucsd.edu/info/vi_tutorial.shtml)

To just create an empty file you can "touch" it:

```
$ touch /path/to/myFile
```

(use sudo if you root owns the directory your touching)

---

### Post by BDNiner on 2008-08-31
I don't know the specific command for vi since I use gedit (it is very similar to notepad). are you working from the desktop and running the terminal emulator or are you working from a text only terminal?

using gedit i would run:
```

gksudo gedit /etc/pm/sleep.d49sound

```
you will then be asked for your admin password. Then copy and paste the file contents into the blank document and then save. you have now created the file in the path you specified. 

*I guess there were some quick typers reading the same post.

---

### Post by Clippy on 2008-08-31
Thank you all so much for your help!  I have now succeeded in creating the file "sleep.d49sound" in the pm directory.

There is one final step in the solution that I am still unsure on.  The solution says to 

> chmod the file as root 'chmod 755 /etc/pm/sleep.d/49sound'.

I'm not sure how to do this I'm afraid.  Can anyone help me with this?

As well, just to make sure I'm doing this correctly, should the file "sleep.d49sound" be inside the folder "sleep.d" (it is currently *inside* the "pm" folder next to the "sleep.d" folder).  And, if so, what would I have to do to accomplish this?  

Thanks!

---

### Post by halitech on 2008-08-31
if the file was actually supposed to be
```
/etc/pm/sleep.d/49sound
``` then what we just did won't work for you. you will need to redo it with the correct path to where the file is supposed to be

far as the chmod
```
sudo chmod +755 /etc/pm/sleep.d/49sound
```

---

### Post by Clippy on 2008-08-31
Thank you halitech for your response.  I've fixed the location of the file and triple-checked everything, and I think I'm doing it right.  Unfortunately, when I entered 
```
sudo chmod +755 /etc/pm/sleep.d/49sound
```
all I got was this:
```
chmod: invalid mode: `+755'
Try `chmod --help' for more information.

```

I also tried inputing this
```
# chmod +x /etc/pm/sleep.d/49sound
```
which is which the second site suggested, but it did not produce anything.

Can anyone help to clarify what I might be doing wrong here, or what I have to do to get the "chmod" command to work?  

(Also, is there a way of checking to see that the overall solution is working as intended, even if it doesn't end up solving my own problem?)

---

### Post by Catalyst2Death on 2008-08-31
I think it should just be:

```
chmod 755 /etc/pm/sleep.d/49sound
```

source:
[http://www.zzee.com/solutions/chmod-755.shtml](http://www.zzee.com/solutions/chmod-755.shtml)

Clarification:

For future reference, file permissions allow or dis-allow users to interact with files.  When you are doing something as yourself (whatever your username is) you only own a handful of files, not the entire operating system.  (I think all you own is /home/(username) but I'm not sure)  So, when you need to modify/edit files owned by the operating system (root) you need to run as the root user.  In most linux flavors, you can change to the root account using the root password.  Ubuntu is set up slightly different.  In order to be more secure, Ubuntu doesn't have an open root account.  This means that no one will be able to hack the root account directly.  Instead Ubuntu uses "sudo" or Super User DO.  This allows you to execute the command following "sudo" as root.  This opens an interesting window.  It allows us to access the root account without it having a password with: "sudo su -" (in english, Switch to the root account as the root user)  **NOTE** don't work day to day as root, in fact unless your doing a lot of work that requires root permissions and you don't want to mess with sudo all the time, stay away from the root account (it could bite you otherwise)

---

### Post by Clippy on 2008-09-01
That worked!  Problem solved! :D

Thank you all for all your help, and explanations.  Not only have I solved a problem that had been bugging me a lot, but I also learned a lot.  This place is great!

Thanks,
Clippy

---

