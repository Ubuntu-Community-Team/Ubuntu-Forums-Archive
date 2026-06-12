---
title: "Help..... Complete newbie"
date: 2008-08-17
forum: New to Ubuntu
---

### Post by imax_tm on 2008-08-17
Im a complete newbie to Linux. But an adept with vista... Hence i have a dual boot. I got bored and wanted something new so i got Ubuntu 8.04. This is where the problem starts after installing no sound and i use ATI so i have ATI FIRE GL problem (God knows what this is) so special effects are disabled. I tried gettin softwares but i have 2 download this is where another problem arises. Im a nigerian residin in nigeria so we only have dail up. Where can i easily download stand alones and get the appropriate drivers i need my sound driver is realtek HD. I also need to know where i can get how 2 connect my nokia phone modem 2 my system. Please i need help urgently. Mails r also welcome my email is [email]imax_tm@yahoo.com[/email]. Please urgent replies are also welcome. Please help this brother out.

---

### Post by Lord Xeb on 2008-08-17
I am not sure about your sound but I think if you were to use this, it may help: [http://ubuntuforums.org/showthread.php?t=879658](http://ubuntuforums.org/showthread.php?t=879658)

You do not need to set up the barry, you need to set up a nokia. Just install kitchen sync, go in and make sure the first member is nokia Mobile Device (gnokii) That will allow you to sync your phone and back it up. But as for adding on apps to the phone from the computer, I am not sure about that.

Also, set up the file sync. It will insure that your contacts and stuff are set up right. If you have questions configuring this or need help with anything that involves my guide, PM me. also you can just copy and paste all the commands into the terminal :D

---

### Post by nicedude on 2008-08-17
For your ATI graphics card try letting envy-ng manage it for you as it will download and install the correct driver without you having to do anything.

TO INSTALL ENVY-NG
sudo apt-get install envyng-gtk

THEN TO RUN IT
sudo envyng-gtk

Then select ATI and let it do its thing


AS FOR YOUR SOUND PROBLEM TRY THIS

sudo alsamixer

in the window that opens see if your sound is turned up, if not turn it up and you will be all good :-)

Hope this helps you out.

---

