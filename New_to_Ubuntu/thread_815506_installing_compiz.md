---
title: "installing compiz"
date: 2008-06-01
forum: New to Ubuntu
---

### Post by eric489 on 2008-06-01
Hi everyone !

I just "converted" to ubuntu about 4 days.:D So now that I installed some programs trough the install/remove application and that i'm starting to acquaint myself to it, I thought I could try installing compiz.
:cool:

After noticing it wasn't available trough the install panel, I finally downloaded it from it's official website. [http://compiz.org/Home/Start](http://compiz.org/Home/Start)

Once the package downloaded, and seeable on the desktop, I clic on it and all I get to my disappointment is the content  of the .tar.gz file ... :(

So I'm asking for your help, if some of you have compiz could they please help me out for the installation knowing that I'm a complete new Ubuntu user.

Thanks a lot for this website.

---

### Post by Troll_the_Great on 2008-06-01
Compiz should be in the repositories, if you using Hardy.Type "beryl" in synaptic and you should find it.If not open "help" in Ubuntu and look for "enabling desktop effects" and it will guide you step by step.In a terminal type "sudo apt-get install  compizconfig-settings-manager" and it should do it.Give it a try.

---

### Post by wolfen69 on 2008-06-01
ubuntu comes with compiz by default. go to system>admin>hardware drivers and install your video driver. reboot. then:
```
sudo apt-get install compizconfig-settings-manager
```
then go to system>preferences>appearance>visual effects

enable advanced. then you can go to system>preferences>advanced visual settings(or something) and enable the effects you want.

---

### Post by eric489 on 2008-06-01
Thanks  for showing me the console installation.

But just one thing, i have only 2 workplaces ( i'm on ubuntu latest version )
so how does the cube thing work then ?

is there a setting activation for switching to 4 workplaces ?

---

### Post by Sef on 2008-06-01
> ubuntu comes with compiz by default. go to system>admin>hardware drivers and install your video driver. reboot. then:
Code:

sudo apt-get install compizconfig-settings-manager



Easier way is Applications > Add/Remove > Show: Change to 'All Available Appliations' > Search: CCSM > click on Compiz Manager box > click apply > apply > close

---

### Post by eric489 on 2008-06-01
Thanks but it's kinda late ... :/ 

I allready installed it trought the terminal.

But thanks a lot for the idea. :)

---

### Post by eric489 on 2008-06-01
I activated the  desktop effects , but as mentionned above, I only have 2 desktop windows.

To run the cube i need 4 right ? So far i've only typed in this command :

sudo apt-get install compizconfig-settings-manager

So what's next ?

---

### Post by philinux on 2008-06-01
Right click the workspace switcher. Prefs.

You need columns 4 rows 1, although you could have a 5 sided cube. It would not be a cube but you get the drift.

---

### Post by Tamjay on 2008-06-01
Go to system>prefrances>compiz settings manager
Choose general options then desktop size
Make your horizontal virtual size 4 and leave the rest at one

Hit back and make sure you have your desktop cube and rotate cube plug ins ticked

<cntrl>+<alt>+left mouse button and voala, cube.

---

### Post by eric489 on 2008-06-01
Thank you, so I have now 4 workplaces :D

But what's next ? 

So far i've only typed this : 

sudo apt-get install compizconfig-settings-manager

rebooted , put the 4 orkplaces and then ?

I still don't see a compiz-fusion application or any kind of shortcut :/ ...

---

### Post by Joeb454 on 2008-06-01
> **philinux said:**
> Right click the workspace switcher. Prefs.

You need columns 4 rows 1, although you could have a 5 sided cube. It would not be a cube but you get the drift.

I had an Octagon when I was running Gutsy ;)

I've not used Compiz since moving to Hardy. And as for your user title - that's what VM's are for - I have a VM running it already, sort of, it's getting update errors ;)

---

### Post by Joeb454 on 2008-06-01
> **eric489 said:**
> I still don't see a compiz-fusion application or any kind of shortcut :/ ...

Click System > Preferences > Advanced Desktop Effects

Now customize away :D

---

### Post by Kinst on 2008-06-01
What's your graphics card? ATI, Nvidia, intel?

You'll probably need a proprietary driver first.

---

### Post by Confazed on 2008-06-01
You should see an advanced effects settings manager under preferences.

Make sure that the Desktop cube and Rotate cube options are selected. 

Then right click on your desktop and select "change desktop effects"

You should see an tab that says visual effects, choose "extra" to attempt to switch to compiz.

If it works you should be able to see the cube by dragging your mouse (with both the left and right buttons pressed simultaneously) or switching workplaces.

Alternatively you can install the compiz fusion icon from synaptic that allows you to switch between compiz and metacity from an icon in the panel.

---

### Post by eric489 on 2008-06-02
> **Joeb454 said:**
> I had an Octagon when I was running Gutsy ;)

I've not used Compiz since moving to Hardy. And as for your user title - that's what VM's are for - I have a VM running it already, sort of, it's getting update errors ;)

What is VM ? :confused:

---

### Post by stchman on 2008-06-02
> **eric489 said:**
> Hi everyone !

I just "converted" to ubuntu about 4 days.:D So now that I installed some programs trough the install/remove application and that i'm starting to acquaint myself to it, I thought I could try installing compiz.
:cool:

After noticing it wasn't available trough the install panel, I finally downloaded it from it's official website. [http://compiz.org/Home/Start](http://compiz.org/Home/Start)

Once the package downloaded, and seeable on the desktop, I clic on it and all I get to my disappointment is the content  of the .tar.gz file ... :(

So I'm asking for your help, if some of you have compiz could they please help me out for the installation knowing that I'm a complete new Ubuntu user.

Thanks a lot for this website.

Compiz is installed by default in Hardy.  Once you have proper drivers for your video card it will be in use.

---

### Post by eric489 on 2008-06-02
> **Confazed said:**
> You should see an advanced effects settings manager under preferences.

Make sure that the Desktop cube and Rotate cube options are selected. 

Then right click on your desktop and select "change desktop effects"

You should see an tab that says visual effects, choose "extra" to attempt to switch to compiz.

If it works you should be able to see the cube by dragging your mouse (with both the left and right buttons pressed simultaneously) or switching workplaces.

Alternatively you can install the compiz fusion icon from synaptic that allows you to switch between compiz and metacity from an icon in the panel.

I'm answered that desktop effects could not be enabled... :(

---

### Post by Joeb454 on 2008-06-02
What graphics card do you have? And do you have the drivers installed for it?

---

### Post by durand on 2008-06-02
Ok, we need to know some system information. Open a terminal (Applications > Accessories > Terminal) then type lspci into it. Copy and paste what it puts out into this thread.

---

### Post by Joeb454 on 2008-06-02
Don't forget to put the output in [code] tags, or it'll be incredibly difficult to read ;)

---

### Post by eric489 on 2008-06-02
It answered this in response to the lspci command.

```
00:00.0 Host bridge: VIA Technologies, Inc. VT8375 [KM266/KL266] Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8633 [Apollo Pro266 AGP]
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
01:00.0 VGA compatible controller: S3 Inc. VT8375 [ProSavage8 KM266/KL266]
```

---

### Post by durand on 2008-06-02
So when you Right Click on Desktop > Change Desktop Background > Visual Effects and change those options, does it do anything?

---

### Post by eric489 on 2008-06-02
I'm replied that the desktops effects could not be enabled ( even when trying to enable the normal mode in visual effects ). :(

And when I do this, this automatically unchecks the cube and rotation mode in Advanced desktop settings. :(

---

### Post by durand on 2008-06-02
Did you do this as in post #3?
**ubuntu comes with compiz by default. go to system>admin>hardware drivers and install your video driver. reboot.**
This is absolutely essential.

Also, what happens when you type glxinfo and try glxgears? Do this after installing the drivers.

---

### Post by eric489 on 2008-06-03
When i open hardware drivers, the list is empty, there is nothing.

So how do i even install a driver ?

---

### Post by Kinst on 2008-06-03
Well what's your video card.

---

### Post by durand on 2008-06-04
> 00:01.0 PCI bridge: VIA Technologies, Inc. VT8633 [Apollo Pro266 AGP]
As stated above.

---

### Post by durand on 2008-06-04
Actually, thinking about it...You should move the thread to this forum: [http://ubuntuforums.org/forumdisplay.php?f=330](http://ubuntuforums.org/forumdisplay.php?f=330) I'm not sure how though. Maybe ask a moderator politely?

---

