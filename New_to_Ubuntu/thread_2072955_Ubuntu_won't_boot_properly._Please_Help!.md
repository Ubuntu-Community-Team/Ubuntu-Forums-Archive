---
title: "Ubuntu won't boot properly. Please Help!"
date: 2012-10-18
forum: New to Ubuntu
---

### Post by ellenw1881 on 2012-10-18
I am new to Linux in general and am not very knowledgeable with computers, however I was able to install it on my Lenovo T400 Thinkpad about 4 or 5 months ago. It has been working fine, and I was on it last night, and it seemed normal. This morning it is a completely other story. I have not been able to boot Ubuntu normally and have not been able to reach the regular desktop. I turn it on and it seems normal at first, and even shows the ubuntu logo like normal, as if it is going to start Ubuntu, but then the screen goes black, and after a minute it goes to a black screen with the following on it.
-----------------------------------------------------------------
*stopping save kernel messages    [OK]
*starting clamAV virus database updater freshclam   [OK]
Speech-dispatcher disabled; edit /ect/default/speech-dispatcher
             checking for unattended upgrades:
                    *starting CUPS printing spooler/server   [OK]
*starting bluetooth       [OK]
*pulseaudio configured for per-user sessions
                 saned disabled; edit /ect/default/saned    [OK]
-----------------------------------------------------------------
That is all it says and then I can type below it. i tried typing cntrl alt f6, and and then it says thinkpadt400 login and i can use my normal login and password that i normally would and then it says welcome to ubuntu 11.10 (GNU/Linux 3.0.0-24-generic i686)
84 packages can be updated 56 updates are security updates. But again, this is all in that same black screen with the ability to type commands below it. I tried to add as much info as I could. I really need help, and I don't know what any of this means and I'm afraid if I try to do something myself I will screw it up more. Thanks in advance!

---

### Post by Bashing-om on 2012-10-18
ellenw1881;

 Panic not. Just proceed in a calm and orderly fashion.  There are solutions.

Let's start and see if you can get your GUI . Then do the updates, see if the updates resolves the situation.
login in to your system from the command line as you did before (user_name password)
then the terminal command 
```
sudo service lightdm start
```do you now have your desk top ?
[INDENT]just try'n to help <==BDQ

[/INDENT]

---

### Post by ellenw1881 on 2012-10-18
Thank you for your reply. I followed your instructions, and unfortunately the situation is still the exact same. Hopefully there is another possible solution?...thanks

---

### Post by ellenw1881 on 2012-10-18
Ok to give you some more info, I did what you said to do, and then it jumped me back to the first black screen that I was at before even doing the cntrlaltf6 and logging in, and said the same thing it said before, so i did cntrlaltf6 and logged in again to see if it still said i had those packages to install, and it still says the same number. It didn't tell me I had done anything when i typed that code in that you gave me either. It also said "lightdm start/running" when I logged back in, so i typed in lightdm start to see if that would get me anywhere and it just tells me "only root can run light display manager, To run as regular user for testing run with the --test-mode flag. As I said, I am not tech savvy at all, so this means nothing to me.

---

### Post by buckyaustin on 2012-10-18
if you get a problem where a gui says you don't have root privileges just put gksudo instead of sudo. This will give you full privileges. Just hope you haven't forgotten the password.

---

### Post by Bashing-om on 2012-10-18
ellenw1881;

Not to stress...if worst comes to worst -> will try re-installing the desk top.
for now let's do the updates, see what results. If there are any errors in the package update process, please post them.
after you login from the login terminal do these commands to update the packages pending. One at a time.
```
sudo apt-get update
sudo apt-get upgrade
```[INDENT]one step at a time ==>BDQ

[/INDENT]

---

### Post by ellenw1881 on 2012-10-18
Ok so I put what bashing said, and then after Austin told me to put gksudo instead to get full access, I typed in "gksudo service lightdm start" instead, and it says "(gksudo:1635): Gtk-WARNING **: cannot open display:"

---

### Post by ellenw1881 on 2012-10-18
Alright bashing. I did exactly what you said, and everything seemed to go smoothly. So now it is updated and upgraded. However, it is still the same when I turn my computer on. Same black screen with the same words. I would love your continued help in the matter, since you seem to know what you are doing and say it in a way I can understand it. Thanks

---

### Post by Bashing-om on 2012-10-18
Thanks, been there done that(at one time I knew nothing!) ,,,Is your graphic card Nvidia ?
If so want you to try this:
reboot and hold shift key as soon as bios screen clears->grub menu
in the grub menu arrow down to a "recovery mode" kernel ->press enter to boot.
once booted into ubuntu:
System Settings->Additional Drivers===>install the recommended driver.
[INDENT]what works,works <==BDQ

[/INDENT]

---

### Post by ellenw1881 on 2012-10-18
OK now I am lost. I got to the grub menu, and went into recovery mode. I am now seeing "recovery Menu (limited read-only menu)" and then there are four options: resume normal boot, check all file systems(will exit read-only mode), remount / read/write and mount all other file systems, and drop to root shell promt. So I don't know how to get to system settings to install the driver. I assume i shouldn't be in the read-only menu, but I don't know how to see anything else, this is all it gives me.

---

### Post by ellenw1881 on 2012-10-18
As for your question about the graphics card, I wouldn't know, but I called the guy who has been inside my computer before and he said he remembers it being a nvidia graphics card, but that it was a while ago and he couldn't say without a doubt. I don't know how I could check that without being able to boot up normally.

---

### Post by Bashing-om on 2012-10-18
my error, think'n to fast huh ? ok...in that secondary menu from the grub menu ..choose "resume normal boot" ///that boots up a vesa driver from the kernel that should give you a desk top...Gui should load...in the launcher (12.04 version) choose System Settings ...and carry on from my last.

sorry to have confused you. ==>BDQ

---

### Post by ellenw1881 on 2012-10-18
Ok so I clicked on resume normal boot and then it takes me to a similar black screen with a command line. This one says
-----------------------------------------------------------------
modem-manager[1004]: <info> Loaded plugin Nokia
modem-manager[1004]: <info> Loaded plugin MotoC
modem-manager[1004]: <info> Loaded plugin X22x
modem-manager[1004]: <info> Loaded plugin Sierra
modem-manager[1004]: <info> Loaded plugin AnyData
modem-manager[1004]: <info> Loaded plugin Huawei
modem-manager[1004]: <info> Loaded plugin Generic
modem-manager[1004]: <info> Loaded plugin Longcheer
Skipping profile in /ect/apparmor.d/disable: usr.bin.firefox
modem-manager[1004]: <info>  (ttys4) Opening serial port...
*starting apparmor profiles   [OK]
*starting clamAV virus database updater freshclam    [OK]
speech dispatcher disabled; edit /ect/default/speech-dispatcher
checking for running unattended-upgrades:
initctl: Event failed
--------------------------------------------------------------
Then I am stuck at this screen and it doesn't do anything else.

---

### Post by Bashing-om on 2012-10-18
lets approach this from a different direction.
1st I do want to know what graphics you are using.
reboot ..to clear all out ...and log back into the login screen
then post back to me the results of these terminal codes:
```

sudo lshw -C display
lspci | grep VGA

```
then I will advise you af an alternative method to attempt to load the desk top.

[INDENT]try'n ->BDQ

[/INDENT]

---

### Post by ellenw1881 on 2012-10-18
I can't figure out that command. I tried a bunch of different ways and it says command not found for all of it. It sounded like you were saying two different commands to use, but I couldn't figure out where the first one ended. I don't know if that line before grep VGA is where it separates. I tried it a bunch of different ways and couldn't get the computer to recognize them as commands

---

### Post by Bashing-om on 2012-10-18
that is 2 commands, 1 per line///
copy and paste into your terminal one line at a time.
copy the line, paste into terminal, hit the enter key

before this is all over you will be command line Sumari !

---

### Post by ellenw1881 on 2012-10-18
nevermind I was making a mistake. ok so I typed in sudo lspci | grep VGA and I got "intel Corporation mobile 4 series chipset integrated graphics controller (rev 07), ATI technologies Inc mobility radeon HD 3400 series."
Then I typed in sudo 1shw -C and i got 
-version print program version (B.02.15)
format can be
-html   output hardware tree as HTML
-XML   output hardware tree as XML
-short  output bus information
options can be
-class CLASS   only shows a certain class of hardware
-C CLASS    same as '-class CLASS'
-c ClASS    same as 'class CLASS'
-disable test   disable a test (like pci, isapnp,cpuid, etc)
-enable test    enable a test (like pci, isapnp, cpuid, etc)
-quiet   don't display status
-sanitize   sanitize output (remove sensitive information like serial numbers)
-numeric   output numeric IDs (for PCI, USB, ect)

---

### Post by Bashing-om on 2012-10-18
ok we know we are running ATI graphics with the radeon driver.
do this and see if you get the GUI:
reboot ->get to grub menu as before, make sure the 1st kernel line is highlighted,
depress the "e" key for "edit" -> arrow down to a line similar to this:
"linux /boot/vmlinuz-3.2.0-24-generic root=UUID=dbd69ed2-530c-4409-8f5a-a3f1ea41fc67 ro quiet splash $vt_handoff" and arrow across and type "nomodeset" - without the quotes- just before the "quiet splash" terms.
ctl-x to continue to boot.
this edit will only have effect for this boot, will cause no harm to your system --

can you now boot to the GUI login ?
[INDENT]thinkin' ==>BDQ

[/INDENT]

---

### Post by ellenw1881 on 2012-10-18
Nope. It changes things a bit, but not much. It brings me to the same black screen but it looks zoomed in I just see the end of the word "server" over on the left, and at the top it says "Ubuntu 11.10", then on the right it says "...*starting CUPS printing spooler/se" it cuts of there, because it is so zoomed in. That's about all that seems to have changed. I typed it exactly how you said to, I'm sure.

---

### Post by Bashing-om on 2012-10-19
To say the least I am surprised ! Not at all what I had anticipated.
I have been looking around about HD 3400 issues -> still not to the point to try a re-install of the desk top, still looking at it as a graphics issue.
Will scratch my head and think on it some more//sleep on it// as it is late here ..I will continue this in my AM ...
[INDENT]progressive logic <====BDQ
 
[/INDENT]

---

### Post by buckyaustin on 2012-10-19
Try the updates as Bashing-om has suggested. If that doesn't work try installing Kubuntu. This will give you an alternative Display Manager. At least that way you should have a GUI. Having a GUI would help with solving the problem with lightDM.

You can do this by typing. "sudo apt-get install kubuntu-desktop".

---

### Post by newb85 on 2012-10-19
It's not really necessary to install an entire DE just for the display manager, when you could simply install the display manager.

KDE Display Manager
```
sudo apt-get install kdm
```

Or you could install Gnome Display Manager (used to be the default in Ubuntu).
```
sudo apt-get install gdm
```

---

### Post by ellenw1881 on 2012-10-19
alright thanks for the replies everyone. I will wait for Bashing to get back on and reply before I do anything else though, just to see what his opinion is on it. If he doesn't have anything else I will try re-installing the display manager, and if that doesn't work, the desktop. I will still have all my downloads right, movies and stuff?

---

### Post by Bashing-om on 2012-10-19
I am back for a short short -- got chores I need to get done - thanks for the vote o confidence//still troubleshooting this as a graphics/driver issue...
I think your card is good as bios screen is good, and text log-in  graphics are good-
I do not think there is any corruption in the desk top files as the update/upgrades went smooth and no errors.
But I am concerned that the use of the"nomodeset" option did not have the desired effect.

so...back to looking at drivers: There are 2 things I want to examine.
1. What driver is loaded: post (copy/paste) the output of:
```
sudo lshw -C display

``` to show what driver is configured;
```
lspci -nnk | grep -iA3 vga
``` to show what driver is in use;
```
lsmod
``` to show what drivers are available.

2. Then I want to apply a different kernel command line option, see what results--pending the results of the above.
[INDENT]we are all in this together ==>BDQ

[/INDENT]

---

### Post by china57 on 2012-10-19
Hi,
reinstall the Operating System. That should solve your problem. This can also be an oportunity, if you so desire,  to install an upgrade. I would recommend to do a clean install, not an upgrade. Which means if it asks is this an upgrade or if there is an upgrade option, ignore it. Click on install. 

When you see a black screen, it's nicknamed the black screen of death. Your comp is about to crash.

I have lived through this several times. I hope this was a help. I thank God for Ubantu. It filled an immediate need. I was pleasantly surprised at how user friendly it has become.

---

### Post by ellenw1881 on 2012-10-19
Ok I typed in sudo lshw -c display and got:
product: mobility radeon HD 3400 series
Vendor: ATI Technologies Inc.
configuration: latency=0 driver=radeon

Then I typed lspci -nnk | grep iAS vga, and I got:
00:02.0 Intel corporation mobile 4 series chipset integrated graphics controller
kernel driver in use: i915
kernel modules: i915
01:00.0 ATI technologies Inc. mobility radeon HD 3400 series
kernel driver in use: radeon
kernel modules: radeon

Then I typed lsmod and got a LOT of stuff so I'm only including what I thought you would need to know:
module: i915, size: 513798, used by: 1
module: radeon, size 933705, used by: 0

---

### Post by Bashing-om on 2012-10-19
looks to me what we have here is a conflict of drivers.
 lshw -c display => no driver is loaded
grep iAS vga => radeon driver and i915
 lsmod => seems to confirm a conflict of drivers 

At this time I want you to copy/paste the full output of 
```
lsmod
```while I scratch my head some more. => BDQ
edit: put this output between the code ("#") tag (top of post)

---

### Post by ellenw1881 on 2012-10-19
_module_         _ size_           _used by_
bnep          ;            17923   ;       2
rfcomm        ;            38408   ;       0
bluetooth                 148869  ;       10 bnep,rfcomm
parport_pc    ;            32114   ;       0
ppdev         ;            12849   ;       0
joydev                    17393   ;       0
binfmt_misc   ;            17292   ;       1
snd_hda_codec_conexant ;   52453   ;       1
arc4            ;          12473   ;       2
snd_hda_intel   ;          28358   ;       0
snd_hda_codec   ;          91888   ;       2 --snd_hda_codec_coexant,snd_hda_intel
snd_hwdep     ;            13276   ;       1 snd_hda_codec
snd_pcm       ;            80435   ;       2 --snd_hda_intel,snd_hda_intel
pcmcia     ;               39822   ;       0 
snd_seq_midi  ;            13132   ;       0
snd_rawmidi    ;           25241   ;       1 snd_seq_midi
psmouse      ;             73673   ;       0
serio_raw    ;             12990   ;       0
snd_seq_midi_event  ;      14475   ;       1 snd_seq_midi
iwlagn        ;            273980  ;       0
mac80211       ;           393421  ;       1 iwlagn
snd_seq        ;           51567   ;       2 --snd_seq_midi,snd_seq_midi_event
thinkpad_acpi    ;        73942   ;       0
radeon        ;            933705  ;       0
nvram         ;            14029   ;       1 thinkpad_acpi
snd_timer      ;           28932   ;       2 snd_pcm, snd_seq
snd_seq_device ;           14172   ;       3 --snd_seq_midi,snd_rawmidi,snd_seq
tpm_tis        ;           14002   ;       0
wmi            ;           18744   ;       0
yenta_socket    ;          27428   ;       0
pcmcia_rsrc     ;          18367   ;       1 yenta_socket
pcmcia_core     ;          21511   ;       3 -- pcmcia,yenta_socket,pcmcia_rsrc
cfg80211     ;             172427  ;       2 iwlagn,mac80211
ttm          ;             65224   ;       1 radeon
i915         ;             513798  ;       1
snd          ;             55902   ;       10 --snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,thinkpad_acpi,snd_timer,snd_seq_device
drm_kms_helper   ;         32889   ;       2 radeon,i915
drm              ;         192194  ;       4 --radeon,ttm,i915,drm_kms_helper
mei             ;          36446   ;       0
soundcore       ;          12600   ;       1 snd
snd_page_alloc     ;       14115   ;       2 --snd_hda_intel,snd_pcm
i2c_algo_bit     ;         13119   ;       2 radeon, i915
video             ;        19069   ;       1 i915
ip               ;         17455   ;       0
parport          ;         40930   ;       3 parport_pc,ppdev,Ip
firewire_ohci    ;         35854   ;       0
firewire_core  ;           56937   ;       1 firewire_ohci
crc_itu_t      ;           12627   ;       1 firewire_core
e1000e         ;           139814  ;       0

---

### Post by Bashing-om on 2012-10-19
the full output says we have both radeon and i915 available:
lets see what we are going to do---
terminal commands:
```
  dpkg -l | grep fglrx
glxinfo | grep direct

```if you are told by the system no can do; install(as advised):
```
sudo apt-get install mesa-utils
```should load the needed drivers.

reboot and lets see where we are at.
[INDENT]learning ==>BDQ

[/INDENT]

---

### Post by ellenw1881 on 2012-10-19
Ok so when i typed those commands it didn't do much except tell me to type exactly what you told me to type sudo apt-get install mesa-utils, because it said glxinfo was not installed. So I typed in the install-utils command and it acted like it was downloading but I see at the bottom it says a line "usr/bin/mandb: can't write to var/cache/man/2034: No space left on device", but then after that it says "setting up mesa utils", so I thought it may not have installed but i restarted and got the same black screen with the same words, I logged in like i did before. I typed in the mesa-utils command again and it said "mesa-utils is already the newest version", so I guess it did install. Also, one thing changed. When I logged in it gave me a notice that the new release "12.04.1 LTS available, run do-release-upgrade to upgrade it" I'm guessing I should do that? Anyway, other than that the black screen is still the same, and I haven't got anything new.

---

### Post by Bashing-om on 2012-10-19
new issue..the no space left on device really bothers me.
How long have you ran this version, ever do any housecleaning ???
not having operating overhead can have all kinds of un-desire-able side affects
checks:
```
df-h
```displays filesystem disk space usage for all the partitions.
```
du -h /home | sort -nr | less
```list disk usage for the /home directory ---change to any-other-directory-of-interest--;
-h renders the output as human readable,the output is then fed into the utility "sort" which organizes the output numerically(-n) and reverses the order (-r) to display the largest files first. Finally the output is fed into the utility "less" which allows you to scroll up and down through the listing. ---pretty nifty huh ???---

updating to 12.04 ...depends, what version are you running at this time? (I strongly adhere to a clean install from cd) 
upgrading- :in the process may resolve the "black screen" issue.

[INDENT]soooo what are we going to do ?==>BDQ

[/INDENT]

---

### Post by ellenw1881 on 2012-10-19
Well most of what I'm using up involves downloads, movies, tv shows, ect. I'm not sure what "housecleaning" involves or what exactly I need to do. I guess I can just re-install with a new disc...but won't this just happen again?

---

### Post by Bashing-om on 2012-10-19
ellenw1881;
off topic here...what version are you currently using...maybe a great advantage to upgrading ...I had reservations going to 12.04 ...I discovered that I really like the new "system" and 12.04 is solid and stable on my system, I rarely revert to others (two others installed) and am finding that unity is a joy to use (and lots more coming).
Disadvantage of upgrading/re-installing -> backing up data and config files -shud be done anyhow--
current install- headroom, really need 20% to operate with (system caching and what not).

drivers: I had entertained the hope that installation of vesa-utils would find/load us a driver....I have a few other things in mind to get a driver loaded...But if you are intertaining the idea of upgrading(good thing)//we will halt cease and desist on this endeavor (no sweat on my part at all). See how your system functions from a live environment from the new version ///.
[INDENT]I am here to help, what do you want to do ? <==BDQ

[/INDENT]

---

### Post by ellenw1881 on 2012-10-19
I am running 11.10 right now. I am fine with updating, I just don't know how to do all the maintenance and clean that cache out. I actually decided to do it a few minutes ago though and I typed in do-release-upgrade, like it said to do to upgrade to 12.04. It says no new release found. So I'm confused why it tells me there is a new 12.04 release and to type do-release-upgrade to get it, but when I type it it says there isn't a new release..

---

### Post by Bashing-om on 2012-10-19
from 11.10 should have no problems upgrading to 12.04 .

It can be done from the command line. See this link:
[http://www.liberiangeek.net/2012/04/upgrade-to-ubuntu-12-04-from-ubuntu-10-04-via-the-terminal/](http://www.liberiangeek.net/2012/04/upgrade-to-ubuntu-12-04-from-ubuntu-10-04-via-the-terminal/)

but I would imagine doing the upgrade from the GUI "update manager" to be quicker and simpler. ( bear in mind I always do my upgrades as clean from install cd's)....
in any event make sure before you proceed that all updates have been done on the current installation. ( as you are short on "head space" I would also make some additional space for the new install...takes more space....
```
sudo apt-get update
sudo apt-get upgrade
```[INDENT]moving on <==BDQ

[/INDENT]

---

### Post by ellenw1881 on 2012-10-19
Alright I will do that. Thanks very much for your time

---

### Post by Bashing-om on 2012-10-19
ellenw1881;

Best to ya ...let me know in this thread how it turns out....I will continue to be interested in your ubuntu relations.

[INDENT]CUL ==> BDQ


[/INDENT]

---

### Post by buckyaustin on 2012-10-23
This has been marked as solved please send a message describing how you solved it for, well my intrest and other people are having the same problem. They need the solution.

---

