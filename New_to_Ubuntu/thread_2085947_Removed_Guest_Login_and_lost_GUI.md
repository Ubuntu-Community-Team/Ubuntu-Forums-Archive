---
title: "Removed Guest Login and lost GUI"
date: 2012-11-19
forum: New to Ubuntu
---

### Post by will547_us on 2012-11-19
I upgraded to 12.10 about a month ago from 12.04.
I'm using a Dell XPS M1330 32 bit w/Intel Integrated Graphics Media Accelerator 3100 per my Dell receipt, but I seem to remember a 965 video card?

I removed my the Guest Login ( it seemed like the thing to do at the time) last evening using these instructions or very close to them:
[B]
"Run the following command in the terminal to open /etc/lightdm/lightdm.conf file in the gedit on your Ubuntu system.

$ gksudo gedit /etc/lightdm/lightdm.conf[/B] [B]

Mine contains only:[/B] [B]
[SeatDefaults]
user-session=ubuntu
greeter-session=unity-greeter
Add the following line to the end of the lightdm.conf file.

allow-guest=false[/B] [B]

Save and close out the opened lightdm.conf file on your Ubuntu system.[/B] [B]

You can either wait until next re-boot or run the following command in the terminal to restart LightDM.[/B] [B]

$ sudo restart lightdm"[/B] 

Guest Login is gone and I can't open Terminal. Gui seemed fine when I logged out last evening but this AM I have no GUI. I'm unable to open Terminal and tty login is not working.

Any suggestions? Help!!

---

### Post by will547_us on 2012-11-19
This must be a hard one or more likely I'm incredibly inept or both??:-k

I'm wondering if you all think I can remedy this by burning an ISO and trying to boot from CD??

To make things more entertaining my wood burning Windows machine's optical drives are kaput so I'd like someone to tell me if this idea is feasible before I go out bumming a PC.

TIA, Will

---

### Post by mikechant on 2012-11-20
Yes, you should be able to fix this by booting from a 'live' CD or USB stick, then check/correct the file you edited.

---

### Post by Bucky Ball on 2012-11-20
Make a LiveUSB instead of a CD if you have no optical drive then boot from that.

---

### Post by steeldriver on 2012-11-20
You should also be able to boot into recovery mode and edit the file from there - if you are comfortable with command line stuff - possibly easier than dealing with a broken DVD drive

HOWEVER I'm concerned that there are bigger issues since the line you added should NOT have broken anything - I tried it on my 12.04 laptop yesterday and it did exactly what it said on the tin (i.e. removed the guest account from the lightdm greeter screen)

---

### Post by will547_us on 2012-11-20
Thank you thank you thank you.:)

Can you expand on how I might try this:
 
> You should also be able to boot into recovery modeI think I checked all my boot options and BIOS but I never saw any "recovery mode" as I had hoped and you are suggesting???

As I look at the gedit I modified I think the line I added was at the beginning instead of the end. Could this be the issue? :confused: 
I'm usually OK working the command line but I'm not too experienced modifying files.

FYI it's the Windows machine with the faulty optical drive and I don't own a memory stick. When I hear back from one of you I'll head over to my sister's and burn an ISO.

Thanks again, Will

---

### Post by Bucky Ball on 2012-11-20
When you boot you should get the menu list where you can choose which OS to boot into. Recovery kernel should be the second Ubuntu entry on the list (ending with 'recovery'). If not, something odd is happening.

If you're not getting this list then hit shift after the BIOS screen and that should bring it up.

Little tip: make it a rule of thumb before editing any file to:
```

sudo cp /path/to/your/file /path/to/your/file.BAK
```This creates a copy of the original in the same directory as the original. For the file you altered it would be:

```
sudo cp /etc/lightdm/lightdm.conf  /etc/lightdm/lightdm.conf.BAK
```If things go pear shaped:

```
sudo cp  /etc/lightdm/lightdm.conf.BAK  /etc/lightdm/lightdm.conf
```... copies the original back.

---

### Post by will547_us on 2012-11-21
Sorry about the PM BB,

Thanks for the last advice re: copying etc. 
I started my machine and held down F12 and I got a black screen with a  long list of Starting different things followed by OK in brackets.  Everything reads OK with the exception of LightDM Display Manager which  first displays as OK then followed by the same and FAIL.
I have a cursor at the bottom of the list. Is this a good place to be and where am I?

TIA, Will

---

### Post by critin on 2012-11-21
> **will547_us said:**
> Sorry about the PM BB,

Thanks for the last advice re: copying etc. 
I started my machine and held down F12 and I got a black screen with a  long list of Starting different things followed by OK in brackets.  Everything reads OK with the exception of LightDM Display Manager which  first displays as OK then followed by the same and FAIL.
I have a cursor at the bottom of the list. Is this a good place to be and where am I?

TIA, Will

When you first boot up and the OS's appear on the screen, where you choose to boot into ubuntu or Windows, there should be a line under the ubuntu entry called 'recovery'.  The word recovery is located at the end of its line.

---

### Post by mikechant on 2012-11-21
> As I look at the gedit I modified I think the line I added was at the beginning instead of the end. Could this be the issue?


Highly likely!

---

### Post by will547_us on 2012-11-21
I apologize I haven't been clear. This is an Ubuntu only machine straight from the factory. There are no OS choices. There is no Recovery Mode that I can find. When I power on the machine I hear the normal start up drill, I see the Ubuntu logo flash once or twice and i end up with a grey screen. If I hold the F2 while powering on I get the blue BIOS screen and if I hold the F12 I get to choose boot order(Internal HDD, CD/DVD/CD-RW Drive, or Onboard NIC. I also can go to the blue BIOS screen or into diagnostics.

I can't get to a Login or Terminal to attempt to correct the LightDM error.

Options, opinions, ideas??

---

### Post by windscape on 2012-11-21
You could try tapping the Esc key right after starting the PC to see if that gets the Grub boot menu to appear, where recovery might be an option. If that doesn't work, then creating a bootable Ubuntu USB drive and booting from that or using another PC to create a bootable Ubuntu CD would be the next thing to try.

---

### Post by Bucky Ball on 2012-11-22
> **will547_us said:**
> ... I see the Ubuntu logo flash once or twice and i end up with a grey screen. 

Yep, right before that, start hitting shift (I think ESC was in older releases but if one doesn't work try the other).

You are not getting a grub menu at boot and you should be. That is why you are not seeing the recovery kernel entry in the list. You are not seeing a menu list. ;)

---

### Post by will547_us on 2012-11-23
Tapping either Esc or F12 during start-up gets me a black screen, scrolling, listing the following:

Starting ClamAV
Starting Name Service Cache
Starting redis-server
speech-dispatcher disabled
Starting Userspace bootsplash
Starting uncomplicated firewall
Starting CUPS printing spooler
Starting System V runlevel compatibility
Starting
Starting crash  report submission daemon
Starting automatic crash report generation
Starting
Starting GNOME Display Manager
Starting LightDM display manager
Starting ACPI daemon

etc, etc ALL of theses lines have [OK] to the right side. Then down 11 more lines there is the LightDM Display Manager  followed by [fail]. Four lines under this is:

Stopping GNOME Display Manager and [OK] to the right.

The next to last line is:

Stopping Recovery options if display manager fails to start and [OK] to the right.  :confused::confused::confused:

Under the last line is a blinking cursor but I can't enter anything here.

Can anyone tell me what this screen is?

Am I completely knackered?

I've been using this PC since Ubuntu 8.04 and I don't ever remember seeing a "Recovery Mode". That sounds like WindowsSpeak to me but I confess to be a bonified newbie comparatively speaking so I'm not going to carve that in stone?

I guess if we're running out of ideas from here I'll make it through the weekend and  head over to HAL-PC to see if maybe someone can figure this out hands on.

Thanks to all of you who offered the benefit of your experience, Will

---

