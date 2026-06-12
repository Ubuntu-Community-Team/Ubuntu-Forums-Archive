---
title: "Nvidia Geforce GTX 570"
date: 2012-02-16
forum: New to Ubuntu
---

### Post by Frimbleglim on 2012-02-16
I am having trouble installing the graphics card drivers from nvidia.  

I downloaded the drivers [here]("http://www.nvidia.com/object/linux-display-ia32-260.19.29-driver.html")

But I don't know what to do with the file.  It seems to be a .run shell script (whatever that means) but it won't open with kpackage kit ("an unknown error happened") or gedit ("could not detect character encoading").  

This is not hugely problematic.  I have a GUI that works after all but having paid for the graphics card it would be nice to use it.

---

### Post by sudodus on 2012-02-16
It is tricky to get the downloaded driver installed. It is much easier to install the built-in proprietary driver. Usually it is even offered automatically to be activated, and is usually working quite well with nvidia cards. Did you try that?

What version and flavour of Ubuntu are you using (vanilla Ubuntu 11.10 or something else)?

---

### Post by haqking on 2012-02-16
> **Frimbleglim said:**
> I am having trouble installing the graphics card drivers from nvidia.  

I downloaded the drivers [here]("http://www.nvidia.com/object/linux-display-ia32-260.19.29-driver.html")

But I don't know what to do with the file.  It seems to be a .run shell script (whatever that means) but it won't open with kpackage kit ("an unknown error happened") or gedit ("could not detect character encoading").  

This is not hugely problematic.  I have a GUI that works after all but having paid for the graphics card it would be nice to use it.

dont know how you managed to get a link to the older version.

anyway it is 295.20 now [http://www.nvidia.com/object/linux-display-ia32-295.20-driver.html](http://www.nvidia.com/object/linux-display-ia32-295.20-driver.html)

download

sh <filename.run>

follow prompts, you may need to blacklist current driver such as nouveau if you have them installed, let the installer do it for you if unsure.

The latest 295.20 is working great for me in slackware across dual monitors, very stable and its an easy install

I am using a gtx 580 but its the same driver, also works well in Debian stable.

The installer is a breeze

Cheers

---

### Post by Frimbleglim on 2012-02-16
I downloaded the file but what now?  I still can't open it.  The messages are the same as those for the older driver.

I am running Ubuntu 10.04 64 bit.  

PS According to the hardware manager "no proprietary drivers are in use on this system".

---

### Post by haqking on 2012-02-16
> **Frimbleglim said:**
> I downloaded the file but what now?  I still can't open it.  The messages are the same as those for the older driver.

I am running Ubuntu 10.04 64 bit.  

PS According to the hardware manager "no proprietary drivers are in use on this system".

what do you mean by you cant open it ?

it is a run file.

you run it like i said in my previous post.

so what messages do you get ?

if you are referring to the messages in your first post, it is not a text file to open with a text editor.

and the readme tells you what to do [http://us.download.nvidia.com/XFree86/Linux-x86/295.20/README/installdriver.html](http://us.download.nvidia.com/XFree86/Linux-x86/295.20/README/installdriver.html)

---

### Post by John Redcorn on 2012-02-16
I am having a similar problem to you and am BRAND NEW. But I think I can help you run the file...

If you right click the file, go to Properties --> Permissions tab at the top  --> Then check the check mark next to the "Allow executing file as program".

Click close, and then double click the file and select the "run in terminal option".

I am running a different version of ubuntu than you, so all of this might be complete trash. So ignore me if I am way off!!

---

### Post by haqking on 2012-02-16
> **John Redcorn said:**
> I am having a similar problem to you and am BRAND NEW. But I think I can help you run the file...

If you right click the file, go to Properties --> Permissions tab at the top  --> Then check the check mark next to the "Allow executing file as program".

Click close, and then double click the file and select the "run in terminal option".

I am running a different version of ubuntu than you, so all of this might be complete trash. So ignore me if I am way off!!

the instructions i posted above.

You dont want to do this when X is running so not a good idea to do it from within GUI

---

### Post by Frimbleglim on 2012-02-16
I can tell that I need to run it but how do I do that?  

I have tried right clicking and opening properties, checking the box "saying allow file to run as a program".  I then right clicked again selected "open" and then Run.  

The dialogue closed but nothing else happened.  "Run in terminal" gave the same result.  

Do I need to use the "Konsol"?  Where can I find out how to do that?

---

### Post by haqking on 2012-02-16
> **Frimbleglim said:**
> I can tell that I need to run it but how do I do that?  

I have tried right clicking and opening properties, checking the box "saying allow file to run as a program".  I then right clicked again selected "open" and then Run.  

The dialogue closed but nothing else happened.  "Run in terminal" gave the same result.  

Do I need to use the "Konsol"?  Where can I find out how to do that?

as i said twice now.

The instructions are on the nvidia webiste where you got the file from.

[http://us.download.nvidia.com/XFree86/Linux-x86/295.20/README/installdriver.html](http://us.download.nvidia.com/XFree86/Linux-x86/295.20/README/installdriver.html)

to run dont do it in X.

and to run a .run file

sh <filename.run>

do it using sudo

---

### Post by Frimbleglim on 2012-02-16
@haqking

I'm sorry but I still don't understand.  I think you are telling me to boot without a GUI and use the comand line to run the file "as root".  

However I don't know how to boot without a GUI starting, how to close the gui once it is started or how to use the command line.

I take it I would have to type in the the directory where the file is downloaded to before I can run it but how would I do that?

---

### Post by Frimbleglim on 2012-02-16
I tried the following: 

Switched on the machine waited for the GRUB menu to appear.  

Selected start in recovery mode from the menu.
Selected drop to shell as root.

Typed "cd /home/hevans/Downloads"
displayed "root@hevans /home/hevans/Downloads #"
Typed sudo sh<NVIDIA.run>
Displayed "syntax error"

What was I doing wrong?

---

### Post by sudodus on 2012-02-16
> sudo sh<NVIDIA.run>
should be
```
sudo sh NVIDIA.run
```

---

### Post by Frimbleglim on 2012-02-16
Ok got it. I caught up with the other thread  Thanks.

---

### Post by haqking on 2012-02-16
> **Frimbleglim said:**
> Ok got it. I caught up with the other thread  Thanks.

the <> i used around the filename example to show it was a filename and needed to be replaced with your specific filename ;-)

Glad you are caught up.

Peace

---

### Post by bogan on 2012-02-16
Hi!** Frimbleglim**.

Don't let the apparent complexities deter you. it is not as difficult as it seems at first.

Open the Home folder from Places menu and check where the .run file has been saved, probably Downloads.
Open a terminal from Applications menu or press Ctrl+Alt+t.

Enter the following, line by line and press 'Enter' after each. do not copy the stuff after the '#' symbols.
```
sudo service gdm stop
``` that is to shut down the graphics Xorg session.
You will be asked for your password, enter it and press 'enter', nothing will show.
```
cd
cd /home/user/Downloads   # where 'user' is your username; change Downloads if that is not where the file is.
dir         # this will check you are in the right place and allow you to check the exact spelling.
sudo chmod a+x NVIDIA-   # Press 'Tab' to complete the file name,and press 'enter'
sudo sh NVIDIA-          # Press 'Tab' to complete the file name,and press 'enter'
```Follow the on screen instructions using the arrow keys to choose the options you want and 'Enter' to activate them.

When it is finished enter:```
sudo service gdm start 
``` and re-boot.

Hopefully that will work OK. if not you may need to set up some blacklists as one of the contributers already said.

Chao!, **bogan**.

---

### Post by josephmills on 2012-02-16
I hope that you dont mind if I step in 

1) download the driver 
2) open terminal and type in 
```
sudo -i
```
then 
```
echo "blacklist nouveau" >>  /etc/modprobe.d/blacklist.conf 

```
then 
```
exit
```
3) Press ctrl+alt+f1 
4) sign in then 
```
sudo  /etc/init.d/gdm stop
```
5) ```
cd ~/Downloads 
```
6)   ```
sudo chmod +x *.sh
```
7) ```
sudo sh nvi*.sh 
``` 
8) reboot after install

---

### Post by bogan on 2012-02-16
Hi!, j**osephmill**s, 

 OP is using 10.04 64 bit, so it will be 'gdm', not 'lightdm', will it not?

Chao!, **bogan**.

---

### Post by haqking on 2012-02-16
> **bogan said:**
> Hi!, j**osephmill**s, 

 OP is using 10.04 64 bit, so it will be 'gdm', not 'lightdm', will it not?

Chao!, **bogan**.

yes it will.

Also the driver install will blacklist nouveau during install if needed, it doesnt really matter either way it will get blacklisted anyways.

Peace

---

### Post by josephmills on 2012-02-16
ok guys I changed it to ```
gdm
``` thanks
I also for got chomod +x that i am putting in now

---

### Post by Frimbleglim on 2012-02-17
Well that seems to have worked.  I installed the drivers using the method **bogan** suggested and now I can turn on the fancy advanced desktop effects.  I still can't see the driver listed under hardware drivers but that doesn't really matter.  

Thank you everyone.  Maybe some day I'll understand what I just did.

---

