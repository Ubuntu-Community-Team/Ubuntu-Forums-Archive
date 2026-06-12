---
title: "Changing Graphic Cards"
date: 2008-08-09
forum: New to Ubuntu
---

### Post by loseby on 2008-08-09
Have swapped from Nvidia to ATI ( 4870 ) and want to know what I need to do. Do I need to uninstall the Nvidia drivers etc and install the ATI drivers ?

At the moment its running in reduced graphic mode.

Thanks

Will

---

### Post by pi.boy.travis on 2008-08-09
Check System-Administration-Hardware Drivers.  I think that :

sudo apt-get auotremove 

will get rid of the old drivers.

EDIT:  Sorry, autoremove is for unused dependencies only.

---

### Post by PmDematagoda on 2008-08-09
> **losbey said:**
> Have swapped from Nvidia to ATI ( 4870 ) and want to know what I need to do. Do I need to uninstall the Nvidia drivers etc and install the ATI drivers ?

At the moment its running in reduced graphic mode.

Thanks

Will

I don't think you have to uninstall the Nvidia driver, as long as X doesn't try to load the Nvidia driver(this is in relation to the xorg.conf file) the two drivers should be in harmony(so to speak).

---

### Post by InfinityCircuit on 2008-08-09
Ubuntu Hardy Heron should be able to install your restricted drivers just fine using jockey-gtk (Restricted Driver Manager).  However, you may have one problem: If it seems like your display just shuts off into power saving mode when you start X, you need to change the DefaultDepth.  Go to /etc/X11/xorg.conf and edit the "Screen" section to include the line DefaultDepth 24.  I have a 3650 myself and it works fine on Hardy (although not on Intrepid)

---

### Post by will_s54 on 2008-08-10
Actually I am unable to install my drivers for the Radeon. And have just had to swap to another computer ( using that ID ) to post this as the screen is now unreadable.

I did a google and tried to follow their instructions but recieved permission errors. Similar thing happened when I put the Graphics Card Installation CD in. It detected it but then something about permision denied yet again.

Maybe I will go back to scratch and format and reintall unless there is an easier way

---

### Post by Methuselah on 2008-08-10
What are you seeing on the ubuntu machine?

---

### Post by loseby on 2008-08-10
Actually I have now managed to get 800x600 resolution  by trying some radeon packages. When you check out screen resolution that is the most available but if enable 3d effects on reboot its failed and before logging on I have to configure the drivers .

Now my card is the Radeon HD 4870 and not been able to set this up easy ( hey in Windows it was a breeze ) is very annoying to say the least.

---

### Post by Methuselah on 2008-08-10
Do you have a widescreen monitor?

---

### Post by loseby on 2008-08-10
yes I have a widescreen ...Dell2408

Just installed and tried using Envy but more errors...Envy doesnt recognise my card as viable with this driver ( driver was 8,06 ) and when I try manualin stallation it fails...something about dpkg failing



enough for now...time to go to windows and enjoy my new card

---

### Post by RiPPeR777 on 2008-09-10
not enough for now man!!!!! Im having the same problems been looking for answers for the past 3 days and I can figure it out. After I used envyNG ubuntu 8.04 first wouldn´t recognize my ATI HD 4870. So I did a manual install with the 8.6 drivers it had. I then restarted my comp and it worked a little. Ubuntu 8.04 recongnized my ati hd 4870 but did not enable 3D acceleration when I did that and restarted Ubuntu didnt recongzied my video card anymore and ask me to pick a different driver. So i pick fglx for it thinking it should work. wrong! I had the same problems as him it would only let me have 800 x 600. can anyone help!!!!!!!!!!!!!!!

---

### Post by markbuntu on 2008-09-10
Envy will not give you the best drivers for your card. You need to follow the instructions here, Method 2. This is especially critical if you are using amd64 Ubuntu:

[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

---

### Post by loseby on 2008-09-11
> **markbuntu said:**
> Envy will not give you the best drivers for your card. You need to follow the instructions here, Method 2. This is especially critical if you are using amd64 Ubuntu:

[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

well will give it a go this weekend if I get the time, anyway have bookmarked that link for later action

Comment :  for Ubuntu to truely compete with Windows drivers for Graphics and soundcards need to be easily available and installable

and thanks

---

