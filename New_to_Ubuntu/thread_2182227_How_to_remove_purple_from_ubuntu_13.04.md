---
title: "How to remove purple from ubuntu 13.04"
date: 2013-10-20
forum: New to Ubuntu
---

### Post by DenyingProduct on 2013-10-20
[SIZE=4]First things first I take no responsibility for anything that may go wrong. As always please back up your data before trying this.
[/SIZE]
Background
I am new to Linux and this forum, I recently received help from this forum and it was one of the best experiences I've ever had on a forum. My problem was resolve and prevented from happening again. Long story short I feel like giving back and this is the only way I know how.

When I first moved over to Ubuntu from Mint the first thing I noticed was all the purple splash screens and all the purple everywhere! I don't like the purple and thus wanted to change it. I found all these solutions online but they were all scattered randomly on different forums and websites. Before anyone post oh that's just the way it is bleh bleh bleh Ubuntu and linux are about freedom and ease if I wanted someone to choose for me i would stay with micros**t.

[U][B]Without wasting more time here we go:
[/B][/U][B]
ALL OF THESE COMMANDS ARE ENTERED INTO TERMINAL <CTR+T> TO OPEN IT
NOTE: sudo runs commands as administrator so be careful when using it, it will prompt you for your password
NOTE: I am using gedit which is the default text editor of ubuntu if you prefer something else be my guess to change gedit to any editor you like
NOTE: I RECOMMEND CLOSING AND SAVING EVERYTHING AND EVEN A GOOD REBOOT BEFORE STARTING
NOTE: Here is a useful website for getting color codes [http://html-color-codes.info/](http://html-color-codes.info/)

[/B]**STEP 1:** Removing splash screen
```
sudo gedit /lib/plymouth/themes/ubuntu-logo/ubuntu-logo.script
```
[B]This will open a window find these values and change it to reflect this
NOTE: this will make it black from purple you may also change it to any color you like. The color is represented with the (0.0,0.0,0.0). note: all 0's is black[/B]
    &#8203;> Window.SetBackgroundTopColor (0.0, 0.00, 0.0);     # Nice colour on top of the screen fading to
    Window.SetBackgroundBottomColor (0.0, 0.00, 0.0);  # an equally nice colour on the bottom
**Now save and close that window and run this to update the changes**
```
sudo update-initramfs -u
```


**STEP 2:** change highlight color when highlighting text or the desktop
```
gsettings set org.gnome.desktop.interface gtk-color-scheme "selected_bg_color:#0489B1;selected_fg_color:#000000"
```
[B]NOTE: selected_bg_color:#0489B1 wil change the highlight to blue and selected_fg_color:#000000" will change text inside the highlight black
[/B]

**Step 3: **removing boot purple
```
sudo gedit /lib/plymouth/themes/default.grub
```
**NOW CHANGE IT TO THIS, SAVE AND CLOSE**
    > if background_color 0,0,0; then
        clear
    fi
**NOW UPDATE CHANGES **
```
sudo update-grub
```


**STEP 4: **login screen,  screen quickly flashes purple before loading default image
```
sudo gedit /usr/share/glib-2.0/schemas/50_unity-greeter.gschema.override
```
**ADD OR EDIT THE FOLLOWING LINE AT THE BOTTOM OF THE FILE**
> background-color = "#000000"
[B]SAVE AND CLOSE THEN UPDATE WITH THIS CODE
[/B]```
sudo glib-compile-schemas /usr/share/glib-2.0/schemas/
```
[B]
STEP 5: [/B]Ubuntu tweak to change default image loaded on log in screen
[B]go download and install ubuntu tweak from [http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)
open it and go to tweaks>login settings the click the unlock on top right
enter your password then at the bottom of the window you can change the default image to anything you like.[/B]

[SIZE=3][B]CONGRATULATIONS YOU KNOW HAVE A MUCH NICER NON PURPLE BOOT EXPERIENCE! YAYAYAY. The point for this next bit of code is to change it from being a nice gui boot with ubuntu logo and circle to being a text based boot that shows you what is happening. Note this is great to diagnosing boot errors. 

Feel free to post any questions!
[/B][/SIZE]

[SIZE=4][B]DO NOT DO THIS IF YOU WANT TO KEEP IT LOOKING PRETTY!
[/B][/SIZE]

**STEP BONUS: **to enable or disable graphic load screen (error reports when off)
```
 sudo gedit /etc/default/grub
```
**NOW FIND THIS LINE AND CHANGE IT TO ONE OF THE FOLLOWING**
> GRUB_CMDLINE_LINX_DEFAUL"quiet splash" // on (logo w/ circles)
    GRUB_CMDLINE_LINX_DEFAUL" " // off (diagnostic text)
**NOW UPDATE IT**
```
update-grub2
```

---

### Post by jakenewkirk on 2013-10-27
Hello jorge4,

I almost have my system looking exactly the way I would like it to except for the stupid purple screen that flashes just before the login 

screen. I tried doing what you instructed to do here (STEP 4: login screen quick purple screen flash before loading default image.) but when 

I try to navigate to the file: 50_unity-greeter.gschema.overrideit doesn't exist. So, naturally, I tried to create it and put background-color= 

"#000000" in the file. Then, I tried to compile it and it gave me the error message: Key file does not start with a group.  Ignoring this file. 

What can I do to overcome this issue? Thank you for your time and I look forward to hearing from you.

---

### Post by jakenewkirk on 2013-10-27
Got this from another post on here and it worked on my system: Ubuntu 13.04 Dell Inspiron 2330

Run 
sudo gedit /usr/share/glib-2.0/schemas/50_unity-greeter.gschema.override


It will open up a blank file with nothing in it. 

Paste this into the file: 

[com.canonical.unity-greeter]
background-color = "#000000"

Click save and close the file.

Run 

sudo glib-compile-schemas /usr/share/glib-2.0/schemas/

just because I'm paranoid I ran these two commands individually immediately afterwards:


update-initramfs -u

update-grub

Hope this helps someone else out there.

---

### Post by DenyingProduct on 2013-10-29
Sorry for the delayed response But i did just try that code to ensure I didn't copy it wrong onto the thread. however everything worked you should get a file with 
> 
[com.canonical.unity-gretter]
background = <dir to your default login background>
icon-theme-name = 'ubuntu-mono-dark'
theme-name = 'radiance'

// this line was the only thing added
background-color = "#000000"


Note: always take advantage of tab complete to ensure the directory of file your talking about is actually there and you can prevent any spelling errors. ex >cd Des{tab} would auto fill >cd Desktop

From the looks of it the other post you found instructed you to do the exact same thing so I am just assuming it was a typo that was messing you up. Best of Luck and enjoy your new personalized Ubuntu :)

---

