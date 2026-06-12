---
title: "Eee PC 900A (Installing Ubuntu)"
date: 2008-10-24
forum: New to Ubuntu
---

### Post by swg2161 on 2008-10-24
Ok Im thinking of getting a Eee PC 900A and I want to install Ubuntu. I would want to install it on the 900A so I dont have to boot from a flash drive. Im confused on how to do this.

Also, will I have to delete the Linux OS that is on the 900A prior to installing Ubuntu or will it just delete it when I install Ubuntu? 

Thanks!!!

---

### Post by eternalnewbee on 2008-10-24
When you install Ubuntu, it will give you the choice whether or not to delete the linux os.
Welcome to the Ubuntu forums btw.
Good luck.

---

### Post by swg2161 on 2008-10-24
I REALLY Appreciate the fast response. I understand the instructions I found to install are as follows: (Will this partition my drive/memory on the EEE PC?)

 Installing Ubuntu on the EeePC

-If your EeePC is turned on, turn it off. Insert the USB flash drive into a USB port on the EeePC. Press the power button on the EeePC, and at the same time, hold down the &#8220;Esc&#8221; key in the upper left corner of the keyboard.

-The EeePC will show the normal &#8220;EeePC&#8221; logo boot screen and then switch to a black screen with a blue menu requesting you &#8220;Please select a boot device&#8221;. Press the &#8220;down&#8221; arrow key to select the name of your USB flash drive and press &#8220;Enter&#8221;. Not all flash drives have the same name, but normally the choice for the USB flash drive in this menu should begin with &#8220;USB:&#8221;. The flash drive will not be labeled &#8220;HDD:&#8221;.

-A black menu with the &#8220;Ubuntu 8.04 on USB&#8221; logo will appear. The menu will give you 5 choices:

&#8220;Try Ubuntu without any changes to your computer&#8221;

&#8220;Install Ubuntu&#8221;

&#8220;Check filesystem for defects&#8221;

&#8220;Test memory&#8221;

&#8220;Boot from first hard disk&#8221;

I select  &#8220;Install Ubuntu&#8221; with arrow keys and press &#8220;Enter&#8221;.

-Lines of black and white code will scroll down the screen, and will soon be replaced with an Ubuntu logo with an orange progress bar. Wait (patiently!) for the progress bar to load, as it can sometimes take quite a while.  Though the progress bar may look stalled, it will move and the Ubuntu installer will load.

-Ubuntu's installer will appear onscreen with a &#8220;Welcome&#8221; message. Select the language you wish to install and click the &#8220;Forward button. Select your time zone and keyboard layouts and click the &#8220;Forward&#8221; buttons again.

-The &#8220;Prepare disk space dialog&#8221;. Here, you have the choice between:

&#8220;Guided - resize &#8230;&#8230;. and use freed space&#8221;

&#8220;Guided - use entire disk&#8221;

&#8220;Manual&#8221;

-You will select &#8220;Guided - use entire disk&#8221;. Once the button next to &#8220;Guided - use entire disk&#8221; is checked, you will be able to choose between two disks: the internal disk on your EeePC (normally labeled &#8220;sda&#8221;) or your USB flash drive (normally labeled &#8220;sdb&#8221;). As we are installing the Ubuntu operating system on your EeePC's internal hard disk, we wish to select the disk that does not have a name reminiscent of the brand name of your flash drive.

-Check the button next to the name of your EeePC's internal disk and click the &#8220;Forward&#8221; button.

BE AWARE THAT AFTER THIS POINT, ALL DATA STORED ON THE EeePC WILL BE ERASED!

A menu asking you to enter your full name, desired username, password and computer name will appear. Enter your information and click the &#8220;Forward&#8221; button. A window listing all of your selected installation options replaces the last one. Press the &#8220;Install&#8221; button.

Ubuntu is being installed&#8230; wait once again&#8230;.

Once Ubuntu has been installed, a dialog informing you that Ubuntu has successfully installed will be presented. Remove your USB flash drive from the USB port of the EeePC and hold down the power button until the EeePC turns itself off. Press the power button again, and the EeePC boot screen will appear, accompanied shortly after by a menu announcing that &#8220;GRUB is loading&#8221; with a countdown. After the countdown completes, the GRUB menu will be replaced with the same Ubuntu logo and orange process bar we saw while installing Ubuntu. Wait (again patiently, this one can also sometimes take some time) for the progess bar to finish, and a prompt for user name and password will greet you.

Ubuntu has successfully been installed!

---

### Post by eternalnewbee on 2008-10-24
Well, congratulations and welcome to Ubuntu. Btw. when your problems are solved you should mark the thread as solved. You can do that from Thread Tools at the top of the page.
Good luck.

---

### Post by swg2161 on 2008-10-24
> **eternalnewbee said:**
> Well, congratulations and welcome to Ubuntu. Btw. when your problems are solved you should mark the thread as solved. You can do that from Thread Tools at the top of the page.
Good luck.

Thanks, Ill do that. I did see one last thing.....I read I have to make Ubuntu 'bootable' from the USB is that correct? Do I just download the file and transfer it to the USB or do I have to do something else? 

Sorry for all the questions. Im a total noob at this.

These are the instructions I found and creating the file on the USB has totally confused me:

[http://wiki.eeeuser.com/installing_ubuntu_8.04](http://wiki.eeeuser.com/installing_ubuntu_8.04)

USB Instructions:
[http://www.pendrivelinux.com/2008/05/08/usb-ubuntu-804-persistent-install-tutorial/#more-387](http://www.pendrivelinux.com/2008/05/08/usb-ubuntu-804-persistent-install-tutorial/#more-387)

Installing Ubuntu 8.04 to the USB flashdrive via Windows:

Download and launch Ubuntup8.exe, a Ubuntu8 folder is created
 
Copy your Ubuntu 8.04 ISO to the Ubuntup8 folder (What is the ISO file?)
 
From the Ubuntup8 folder, click fixu.bat and follow the onscreen instructions
 
Once the fixu.bat script has finished, navigate to the new USB-Ubuntu folder inside the Ubuntup8 folder
 
Copy all of the files from "within" the USB-Ubuntu folder to the "root" of your flash drive (not to a subfolder)
 
Restart your PC and set your BIOS or Boot Menu to boot from the USB device
 
If all goes well, you should be able to Run Ubuntu in Persistence Mode saving changes.

---

### Post by swg2161 on 2008-10-24
Ok the instruction in the above post I dont understand. It says to "Copy your Ubuntu 8.04 ISO to the Ubuntup8 folder" so where or what is the "Ubuntu 8.04 ISO"?

It also says to "Copy all of the files from "within" the USB-Ubuntu folder to the "root" of your flash drive (not to a subfolder)" - this I could not get to work so I assume I screwed up a step. 

:(

I think this is way above me to do. Are there more ...um..'dumb'ed down' directions? Im thinking the directions I listed above arent the right ones.

---

### Post by eternalnewbee on 2008-10-24
Sorry for my late reply. Unfortunately I don't have any experience installing from usb drive either.
But I do have experience installing from a cd. What I would do is download the stable version of Ubuntu here: [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download).
Then burn at speed 4 or 8 and boot it.

---

### Post by eternalnewbee on 2008-10-24
Btw, I read the instructions you read from the website, and they are as abracadabra to me as they are to you

---

### Post by swg2161 on 2008-10-24
> **eternalnewbee said:**
> Btw, I read the instructions you read from the website, and they are as abracadabra to me as they are to you

Well I think I got it all copied correct. I found the .ISO file (it was a large download) The last thing it says to do is this:

"-Once the files are copied to the flash drive, open the flash drive in Windows Explorer and run the “makeboot.bat” script. Follow the script prompts and wait until the script finishes. Once the script has finished, eject your USB flash drive. 

Your USB flash drive is now a bootable Ubuntu 8.04 LTS install disk! "

I just need to know how to run the "makeboot.bat" script. And then I think Ill have it.

---

### Post by eternalnewbee on 2008-10-24
You'll have to open it from a terminal.
It's been two years since I last used windoze, so if memory serves me correctly you have to click Start > Run, but I'm really just guessing.

---

### Post by swg2161 on 2008-10-24
> **eternalnewbee said:**
> You'll have to open it from a terminal.
It's been two years since I last used windoze, so if memory serves me correctly you have to click Start > Run, but I'm really just guessing.

Ok, I did that and the terminal window..or what ever the DOS looking window is...comes up but it say "Parameter required" and then it say "Aborted"

And I REALLY appreciate your patience and help with this.

---

### Post by swg2161 on 2008-10-24
Here is what I did:

-On your Windows computer, download the UB8Convert utility from Pendrivelinux.com and run UB8pconvert.exe. A folder called “Ubuntu8” will be created on your Desktop. Place your .iso file containing Ubuntu inside the “Ubuntu8” folder. 

-Run the “fixu.bat” script inside the “Ubuntu8” folder. Read through the prompts and wait until the script has successfully terminated. After the script finishes, a new folder called “USB-Ubuntu” will be created in the “Ubuntu8” folder. 

-Insert your USB flash drive into the USB port on your Windows computer. Copy all the files in the “USB-Ubuntu” file onto your flash drive. All files copied must be copied to the root directory of the flash drive, not another folder. 

**_*-Once the files are copied to the flash drive, open the flash drive in Windows Explorer and run the “makeboot.bat” script. Follow the script prompts and wait until the script finishes. Once the script has finished, eject your USB flash drive. *_**

The above in **BOLD **is the issue I am having

---

### Post by eternalnewbee on 2008-10-24
Did you open the terminal and typed: > UB8pconvert.exe. 

---

### Post by eternalnewbee on 2008-10-24
And don't worry about my patience. I worry about wether I'm helping you get it right.

---

### Post by swg2161 on 2008-10-24
> **eternalnewbee said:**
> Did you open the terminal and typed:

no it didnt let me type anything. It just said "Parameter required" and then it say "Aborted"


I wonder....hmmmmmmm

---

### Post by eternalnewbee on 2008-10-24
I wish some wizards were awake to help you out..
When you click on Run you get the command prompt, right?

---

### Post by swg2161 on 2008-10-24
> **eternalnewbee said:**
> I wish some wizards were awake to help you out..
When you click on Run you get the command prompt, right?

YES. That is correct. I followed the instructions I posted earlier and it appears I have everything properly copied to my USB. I just cant figure out if the USB will be bootable or if I need to do another step regarding the instructions to run a makeboot.bat script....however that is done.

---

### Post by eternalnewbee on 2008-10-24
Trial & Error: Just try it. reboot and see what happens.:)

---

### Post by swg2161 on 2008-10-24
> **eternalnewbee said:**
> Trial & Error: Just try it. reboot and see what happens.:)


Ok..I have to wait until tomorrow to do it. Ill update when I try it. 

thank you!

---

### Post by eternalnewbee on 2008-10-24
Btw, you did follow the "bold" instructions, didn't you?

---

### Post by eternalnewbee on 2008-10-24
OK, good luck.

---

### Post by swg2161 on 2008-10-24
***_-Once the files are copied to the flash drive, open the flash drive in Windows Explorer and run the “makeboot.bat” script. Follow the script prompts and wait until the script finishes. Once the script has finished, eject your USB flash drive. _***

This is what Im not sure about. I opened the USB flash drive in explorer...but not sure if Im running the makeboot.bat script right. The makeboot.bat script DOES run but in the terminal window it says:

[B]Parameter required....(see readme.txt)
[aborted]
Press any key to continue...[/B]

---

### Post by eternalnewbee on 2008-10-24
Then I'm at a loss too and can only recommend what I did earlier on, and that's to download Ubuntu from here: [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download), burn at a low speed and boot the CD...

---

### Post by swg2161 on 2008-10-24
> **eternalnewbee said:**
> Then I'm at a loss too and can only recommend what I did earlier on, and that's to download Ubuntu from here: [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download), burn at a low speed and boot the CD...


my desktop is a windows machine. If I make a CD, how do I install that on to the eee PC 900A? :confused:

---

### Post by eternalnewbee on 2008-10-24
Well, I assume you can insert a cd into it...
( sorry if this looks sarcastic, but it really isn't. The fact that you are getting this late reply, is because I went to look for Hardware specifications, but couldn't determine wether it has a cd or dvd drive ).

---

### Post by eternalnewbee on 2008-10-24
Anyways, just restart, and boot from the CD. Meaning that the screen you should see is the Ubuntu boot screen.

---

### Post by starcannon on 2008-10-24
This may help, and you can do it from a ubuntu livecd usin your desktop computer to make your liveusb stick to install on your eee.
[http://klik.atekon.de/liveusb/](http://klik.atekon.de/liveusb/)
Anyway give that a shot, it will require you to download and burn the livecd, then boot from the livecd on the desktop computer.

Eternalnewbie, the eee notebooks have no optical drive, so either a usb cd drive, or a liveusb stick, or a net install is about all you can do(listed in order of easy).

GL, read directions thoroughly, and not a bad idea to back up any data on the host just in case.

---

### Post by Aedes on 2008-10-24
I just installed Ubuntu eee on my 900A the other night.  To prepare the USB drive I used a program called UNetbootin. ([http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/))
It comes in both windows and linux versions, and was very easy to use.

---

### Post by eternalnewbee on 2008-10-24
Thanks for the info, and for pointing swg2161 in the ( hopefully ) right direction.

---

### Post by t0p on 2008-10-24
Another link for the OP: [http://www.pendrivelinux.com/2008/05/08/usb-ubuntu-804-persistent-install-via-the-live-cd/]("http://www.pendrivelinux.com/2008/05/08/usb-ubuntu-804-persistent-install-via-the-live-cd/")

That's how I installed ubuntu onto my Eeepc 701.  I assume you have an ubuntu live cd?  Cos you'll need one to do this.  But it's simple enough to download the .iso.

Then, to get it all to work with the hardware, I followed the instructions [here]("http://wiki.eeeuser.com/getting_ubuntu_8.04_to_work_perfectly?s=ubuntu%20eee%20riceeey").

Now, ubuntu works just fine on my Eeepc.

---

### Post by swg2161 on 2008-10-24
> **t0p said:**
> Another link for the OP: [http://www.pendrivelinux.com/2008/05/08/usb-ubuntu-804-persistent-install-via-the-live-cd/]("http://www.pendrivelinux.com/2008/05/08/usb-ubuntu-804-persistent-install-via-the-live-cd/")

That's how I installed ubuntu onto my Eeepc 701.  I assume you have an ubuntu live cd?  Cos you'll need one to do this.  But it's simple enough to download the .iso.

Then, to get it all to work with the hardware, I followed the instructions [here]("http://wiki.eeeuser.com/getting_ubuntu_8.04_to_work_perfectly?s=ubuntu%20eee%20riceeey").

Now, ubuntu works just fine on my Eeepc.

No I dont have it on a CD. What is a Live CD? Im sure I sound stupid but I have NO exp with Ubuntu. Im thinking I should probably just not do this since Im totally lost now. The instructions Im reading is greek to me. I do appreciate everyones help.

---

### Post by swg2161 on 2008-10-24
> **Aedes said:**
> I just installed Ubuntu eee on my 900A the other night.  To prepare the USB drive I used a program called UNetbootin. ([http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/))
It comes in both windows and linux versions, and was very easy to use.


I downloaded this as well. Are there step by step instructions for this? Like what to select for the kernel option and such?

---

### Post by t0p on 2008-10-24
When I said you need the live cd, what I meant was, you need to download the ubuntu live cd .iso, which is available from [this link]("http://www.ubuntu.com/getubuntu/download").  You won't need to burn it to a cd, as you want to transfer it to a usb stick.  There are detailed instructions on how to do this at the link I gave you in my previous post, or [you can use Unetbootin]("http://unetbootin.sourceforge.net") as suggested by Aedes.

You asked for a step-by-step guide to using Unetbootin.  I don't know about that.  But I have used Unetbootin before, and I found it to be pretty self-explanatory and easy to use.  The instructions I linked to at [www.pendrivelinux.com]("http://www.pendrivelinux.com") aren't too complicated either.  But if you run into problems with either method, don't hesitate to ask for help here.

---

### Post by swg2161 on 2008-10-24
well again I cant thank everyone enough for all the help. I was worried I'd get flamed. Putting myself in your shoes having reading my posts must leave some of you scratching your heads.

---

### Post by swg2161 on 2008-10-24
I downloaded the Ubuntu .iso from t0p's link above,

Im using Unetbootin now. I ran Unetbootin and selected the .iso file I downloaded. It looks like it worked. (Crosses fingers)

Its on my USB! 

It says now in Unetbootin:

[B]After rebooting, select the USB option in the BIOS menu.
Reboot Now?[/B]

DO I just take the USB out (without rebooting my desktop PC) and put in the 900A and reboot?

Also when I view my USB (F: Drive) in My Computer it shows the Ubuntu logo now! Is that good?

---

### Post by eternalnewbee on 2008-10-24
Back again. Do it. Reboot the system and go into the BIOS. Press F2 or F11 and select the usb device, save and exit.

---

### Post by eternalnewbee on 2008-10-24
Hold on. If you take the USB out you won't be able to boot from it.

---

### Post by swg2161 on 2008-10-24
> **eternalnewbee said:**
> Hold on. If you take the USB out you won't be able to boot from it.

Now Im confused again...

I dont want Ubuntu on my desktop...I want it on the 900A...

I use my desktop to make the USB drive Ubuntu bootable.

Then it goes into my 900A which I reboot..not left in my desktop to reboot...right?

---

### Post by eternalnewbee on 2008-10-24
OK, just follow the advice you were given. I'm not sure either and in my enthusiasm to be back online I might have overlooked something.

---

### Post by swg2161 on 2008-10-24
Well here is what I did......

I did a test a rebooted my windows desktop from my USB. Guess what? It brought up the Ubuntu Install screen!

So now it should work on the 900A too right??? :D

---

### Post by eternalnewbee on 2008-10-24
Keep smiling. My fingers are crossed, too. Cross-fingered typing.... Just kidding.
Good luck Earthling.
Let us know your progress.

---

