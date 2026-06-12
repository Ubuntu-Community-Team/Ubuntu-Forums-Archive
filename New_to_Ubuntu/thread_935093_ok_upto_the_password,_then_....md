---
title: "ok upto the password, then ..."
date: 2008-10-01
forum: New to Ubuntu
---

### Post by voithia on 2008-10-01
Dear friends, I have been looking up previous threads and trying some of the suggestions but getting nowhere.
I've been using Ubuntu since July, now when I log in with username and password, it takes minutes for the bird to appear and then without any panels, so can do nothing but restart. If I install ubuntu again, I assume that I'll lose the programs etc that I've installed since July.
Is there a way around this? Can the already installed Ubuntu be fixed?
Also, the light on the comp HD stays on.

---

### Post by Nxion on 2008-10-01
Hi !

What window manager are you using? Are you using KDE? Gnome? or something different? Also what variant are you using? Ubuntu? Kubuntu? Xubuntu?

Thanks

---

### Post by Nxion on 2008-10-01
> If I install ubuntu again, I assume that I'll lose the programs etc that I've installed since July

Yes, you would lose everything If you reload, but there is always way to backup the packages you have loaded and reload them.

> Also, the light on the comp HD stays on.

This sounds like to me it might be a hardware issue. How old is computer? And what kind is it? Dell? HP? or a clone?

Thanks

---

### Post by Orange_and_Green on 2008-10-01
Does it get any better if you start Ubuntu using a previous kernel (the GRUB boot loader should present you with a list of all installed kernels, try running one a little down in the list), or at least in safe mode?

I developed a tool that creates backup scripts so you don't have to reinstall your programs manually, you can find it here:

[http://ubuntuforums.org/showthread.php?p=5818826]("http://ubuntuforums.org/showthread.php?p=5818826").

If you have your home on a separate partition, just backing up the script my program will give you and possibly a few other config files if you modified any (such as /etc/sources.lst if you added repositories and such), reinstalling should not be so much of a pain (at least, I designed the program specifically with this hope in mind).

However, reinstalling really is an option of last resort so I would be happy if we can troubleshoot your current ubuntu instead...
Good luck & keep us posted:KS

PS [This thread]("http://ubuntuforums.org/showthread.php?t=678665") also has another very nice backup project going, be sure to check it out

---

### Post by voithia on 2008-10-01
Hi Nxion, 

My computer is a 3 year old clone.The problem may well the hardware  The os is Ubuntu and the windows manager is Gnome. Thanks! 

Hi Orange and Green

I'm looking at that thread now. Thanks!

---

### Post by Orange_and_Green on 2008-10-01
You're welcome, I hope you find it useful.:KS

Did you have any luck with logging in in safe mode and/or with a previous kernel version?

---

### Post by voithia on 2008-10-01
Yes, but it comes to the same condition after name/password.
I tried waiting it out for about 30 minutes and it gave me a white panel (blank) above and another (also blank) below the bird. 
I'm using the cd at the moment and sorely tempted to just reinstall.

---

### Post by Orange_and_Green on 2008-10-01
Oh dear, 30 minutes... I'm really sorry you are having such a strange behaviour...

If you press ctrl+alt+any of the F keys from F1 to F6, you can login into a different terminal. From there, you could try running "top" to see if there are any processes taking up the lot of the system resources, and then "kill PIDnumber" or "killall processname". ("kill -s 9 PIDnumber" or "killall -s 9 processname" if it doesn't want to die:twisted:)

You can then press ctrl+alt+F7 to turn back to the "normal" desktop.

Also, you could try hitting alt+f2 when the bird shows up and type "metacity --replace" to kill off compiz and see if that does the trick.

If not, please download my program, run the "aptautosave" binary from one of the "F key terminals" (actually tty1 through 6), and get at least the restore script for your packages from the aptautosave directory in your home...

Two thumbs up and all other fingers crossed :KS

---

### Post by voithia on 2008-10-01
Thanks for those suggestions, I've already tried the thumbs and fingers -  the thumbs are ok and it's painless when the fingers of one hand are crossing the fingers of the other. I'll try them all out by tomorrow.

---

### Post by voithia on 2008-10-02
Unsolved. I'm going to save what I can and re-install.

---

### Post by LastWho on 2008-10-02
no dont

just wait lol i ll try to help :p

---

### Post by LastWho on 2008-10-02
ok **first** lets try this:

Log in...

Ctrl-Alt-F3

then name and password
then type this:
```
export DISPLAY=:0
```then 
```
metacity --replace
```Ctrl-Alt-F7 to get back and check if it gives a result





Edit: you ve been for too long lol

Here are my next suggestions:

if **first** doesn't work try **this**:

[INDENT] Ctrl-Alt-F1 

enter username and passw

then type:
```
sudo apt-get install ubuntu-desktop
```if it asks you something say yes.. and enter

at the end type this:
```
sudo /etc/init.d/gdm stop
```Then
```
sudo /etc/init.d/gdm start
```
to get back and check: Ctrl-Alt-F7
(also you may want to restart your pc to see if it works)
[/INDENT]    

If **this** doesn't work even after restart, try **that** :D 
before you log in:

[INDENT] Ctrl-Alt-F1

username and pass

type:
```
lspci | grep -i vga
```its to ve the name of your video card, you may need it for the next step.. write it down then move to next,

type
```
sudo dpkg-reconfigure xserver-xorg
```that ll reinstall your xserver
use (tab) tabulation to select ok, yes, or no .. and choose the best of your keyboard ...

Ctrl-Alt-F7 tthen log in to check if it works (at log in you may be asked to select a video card.. etc)

...
[/INDENT] 

     
what is amazing about linux is it flexibility, once you ve a prb or you messed up something you rarely need to reinstall it like windows.. and once you learn from your faults the tricks that took you hours to apply become reflexes!!

Edit: Ryadt is here!! you re saved ;)

---

### Post by voithia on 2008-10-02
Dear LastWho

Tried that and got this message 

"invalid MIT-MAGIC-COOKIE-1 keyWindow manager error: Unable to open X display :0"

Many Thanks for trying

---

### Post by Ryadt on 2008-10-02
Did you try to install the gnome panel.```
sudo apt-get install gnome-panel
```get install

---

### Post by LastWho on 2008-10-02
I believe he/she has the same issue i had this morning Ryadt! :KS

---

### Post by voithia on 2008-10-02
I keep having to restart the pc so I can load the liveuser cd and internet, waiting for the HD for Ubuntu... everything is going slow which made me desperate enough to reinstall- the waiting and switching - ugh!

Anyway I will try your suggestions and let you know how it goes tomorrow. Thanks!

---

### Post by LastWho on 2008-10-02
ok Voithia ;)
but please don't reinstall lol doing so will offend these two guys:

[IMG]http://upload.wikimedia.org/wikipedia/commons/thumb/f/f4/Richard_Matthew_Stallman_cropped.jpeg/150px-Richard_Matthew_Stallman_cropped.jpeg[/IMG] [IMG]http://upload.wikimedia.org/wikipedia/commons/thumb/7/71/Linus_Torvalds_cropped.jpeg/150px-Linus_Torvalds_cropped.jpeg[/IMG]
:KS:popcorn:

---

### Post by voithia on 2008-10-03
I have not been able to properly carry out all your suggestions, because I get the message that sudo is not available.

I am also getting these error messages (among others) " fsck died with exit status 4"

and "file system check failed"

I am far from discouraged with Linux and the last thing I would wish is to cause any offense so I will persevere with recovery through today and the weekend - no time tomorrow, just Sunday. If it comes to re-installing, and I do so successfully, it too will be a useful lesson.

My brother-in-law (at my request) installed Ubuntu for me.

---

### Post by LastWho on 2008-10-03
I hope you will get a help soon, or you will succeed reinstalling it
regards

---

### Post by Nxion on 2008-10-03
Sorry it has taking me so long to reply. Well I would say that a reload is your best bet at the moment. But to be honest it sounds to me like your might have a bad hard drive or a bad controller. Do you have any thing to run diagnostics on your machine?

---

