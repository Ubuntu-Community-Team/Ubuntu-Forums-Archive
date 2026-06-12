---
title: "downloaded apps appear in task bar on left of desktop,but no GUI appears"
date: 2014-06-11
forum: New to Ubuntu
---

### Post by Un_Known on 2014-06-11
iinstalled 14.04 today,and been looking forwardto it,however i am finding that none of the apps i have installed load their GUI onto screen.
they do appear on the left hand task bar.  (vlc,deluge torrent handler, transmission torrent handler, and a good few more)
when i tried to launch deluge,for eg, it appears on task bar,and when i click on it to get the menu, either nothing happoens, or screen darkens in tone as if it were "freezing up".

it also so happens that many things are taking a long time to laod. lots of that little spinning wheel.
any advice? please keepit simple as i am a total novice with ubuntu yet. i am so keen to get this nOS upand running fully.been looking very forward toit.
thank you allvery kindly.

---

### Post by Un_Known on 2014-06-11
a further issue i am having is that,for eg,when i am trying to download a torrent from a torrent link,when i click the link i get the "launch application" dialogue window and guess what,it dosnt show the apps i need,and it is not at all obvious where to find them in there. may just be my lack of ubuntu knowledge,but seems impossible.
any hints?
there are a few more related problems, but dont wanna crampo you all,and am very tired.been trying to figure this stuff out all night.

---

### Post by Un_Known on 2014-06-11
further info to apps not showing up. when i click their icon,or right click and get menu, the screen fades,and a top bar appears for them (you know,the one with the cross,minus sign,and square to minimize,expand,or close giu etc,but nothing apopears in that faded space.

---

### Post by oldrocker99 on 2014-06-11
The Unity desktop has its quirks; you might want a more traditional one. Try this:
```
sudo apt-get install xubuntu-desktop
```

Hit Y when it asks, and let it download and install. Then log out and select "Xubuntu" from the button by your login. Log in and see if you like XCFE (the desktop used in Xubuntu) better.

---

### Post by Un_Known on 2014-06-11
ok,am not sure i understand this fully,or which aspect of my problems it helps heal. but i suppose i can try.thanx.
OH,log out?log out of what? and log into what?

---

### Post by yancek on 2014-06-11
You can launch an application by clicking on the dash-home icon, the Ubuntu logo in the extreme upper left of the Desktop.  When it opens, there is a Search box.  Type the name of the app and its icon should appear, just click it.  You can also open in a terminal by giving the full path as with vlc:  /usr/bin/vlc.  If you don't know where the app is, do whereis vlc to find the path.

---

### Post by Un_Known on 2014-06-12
> **yancek said:**
> You can launch an application by clicking on the dash-home icon, the Ubuntu logo in the extreme upper left of the Desktop.  When it opens, there is a Search box.  Type the name of the app and its icon should appear, just click it.  You can also open in a terminal by giving the full path as with vlc:  /usr/bin/vlc.  If you don't know where the app is, do whereis vlc to find the path.

yes, i knew that. thank you,but it dosnt really appear to answer much of my problems yancek. and dosnt answer why this is happening or how the actual prolem/s can be genuinely fixed.

also,i installed museek, (i have used soulseek for years, so know how it works),and it wont connect.in fact many of my devices that need to connect to the net,dont,even thoi tried switching the firewall off
most of my apps dont work,even the native ubuntu movie player dosnt really work and cant load multiple files.

---

### Post by Un_Known on 2014-06-12
> **oldrocker99 said:**
> The Unity desktop has its quirks; you might want a more traditional one. Try this:
```
sudo apt-get install xubuntu-desktop
```

Hit Y when it asks, and let it download and install. Then log out and select "Xubuntu" from the button by your login. Log in and see if you like XCFE (the desktop used in Xubuntu) better.

i would like to try this,but which issue is it refering to? and what does it do?  i would rather fix what i have BEFORE i try another desktop. i dont want to get into desktop fan clubs just yet.no offense intended.

ah, to heck,i'll just try that now! ..........
seemed to install! not sure what to do now though.
last section of terminaltxct said this:
etting up xubuntu-docs (14.04.1) ...
Setting up xubuntu-icon-theme (14.04.2) ...
Setting up xubuntu-wallpapers (14.04.2) ...
Setting up brltty-x11 (5.0-2ubuntu2) ...
Setting up gnome-system-tools (3.0.0-3ubuntu4) ...
Setting up ristretto (0.6.3-2ubuntu1) ...
Setting up xbrlapi (5.0-2ubuntu2) ...
Setting up xfce4-places-plugin (1.6.0-1ubuntu1) ...
Processing triggers for initramfs-tools (0.103ubuntu4) ...
update-initramfs: Generating /boot/initrd.img-3.13.0-29-lowlatency
Processing triggers for libc-bin (2.19-0ubuntu6) ...
so i guess thats correct?

---

### Post by 3rdalbum on 2014-06-12
What happens when you launch one of those misbehaving programs from the terminal? Does the GUI work then, and if not are there any error messages in the terminal?

---

### Post by jdeca57 on 2014-06-12
If I understand main question correctly, the answer - to get icons on the desktop - is [http://askubuntu.com/questions/450266/an-easy-way-to-create-a-desktop-shortcut](http://askubuntu.com/questions/450266/an-easy-way-to-create-a-desktop-shortcut)

---

### Post by Un_Known on 2014-06-12
> **3rdalbum said:**
> What happens when you launch one of those misbehaving programs from the terminal? Does the GUI work then, and if not are there any error messages in the terminal?

sounds like a great idea!!!
though i'm afraid i'm still a bit of a panzy when it comes to terminal literacy.but i do like this idea. thanx

---

### Post by Un_Known on 2014-06-12
now rythmbox wont load onto desktop,just getting it on left taskbar,

---

### Post by Un_Known on 2014-06-12
> **jdeca57 said:**
> If I understand main question correctly, the answer - to get icons on the desktop - is [http://askubuntu.com/questions/450266/an-easy-way-to-create-a-desktop-shortcut](http://askubuntu.com/questions/450266/an-easy-way-to-create-a-desktop-shortcut)

cool!i like it!!
the main issue really is that no apps actually run,apart from appearing in the launcher baron the l;eft of screen.
in short i cant use anything!!! well,no tmuch. and many of the apps that do appear/load on desktop dont function too well. eg,museek wont connect or certain function are greyed out,that is inactive/locked.

---

### Post by wolflint on 2014-06-12
Have you got 2 monitors?

---

### Post by wolflint on 2014-06-12
Actually that probably has nothing to do with it sorry.

---

### Post by mc4man on 2014-06-12
You may be running with lvmpipe which is generally slow & unusable  - 
Open a terminal (ctrl+alt+t
copy & paste this command, press enter. See if you get any no's
```
/usr/lib/nux/unity_support_test -p
```

Also  post output of  - 
 ```
sudo lshw -C display
```

---

### Post by Un_Known on 2014-06-12
AH! incidently mwcerrana! i do technically speaking use two monitors, yes.my main laptopmonitor has damage on it,so i use an auxilliary one to compensate!
it is possible that wouldsomehow upset the actual running of the system?
weirdly interesting!!!!!!! any further info there may help if its releveant?

---

### Post by Un_Known on 2014-06-12
hey mc4man! yes,i tried running those commands, and the first one, "test p" gave me all yes's,and the 2nd,a long list. it goes thusly:

 *-display:0             
       description: VGA compatible controller
       product: Mobile 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:45 memory:f0000000-f03fffff memory:d0000000-dfffffff ioport:1800(size=8)
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
       resources: memory:f0400000-f04fffff

it'sa bit ofa mouthful,and i wouldnt know if anything is wrong there. what you think?

---

### Post by Un_Known on 2014-06-12
i may try this suggestion in a day or two.may just see how if this fixes first,just as much for learning as just simply to fix. thanx tho! appreciated

---

### Post by Un_Known on 2014-06-12
ahhhh! so the paths to apps goes in that manner? cool! thanx!
will try that for sure,tho its a hassle having to do that allthe time,it may help.
the first suggestion i have tried, using the dash! it sometimes worked,but still mostly got the same glitches.

---

### Post by Un_Known on 2014-06-12
i just tried using the command/path forvlcyou mentioned,and it didnt work i'm afraid.it LOOKEd as though it would,but no.
the prompt gave me these reseults:
/usr/bin/vlc
VLC media player 2.1.4 Rincewind (revision 2.1.4-0-g2a072be)
[0xc68118] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
but i onlygotan icon on the launch bar,and an icon up top left on the black bar.
any ideas what is wrong there?

---

### Post by Un_Known on 2014-06-12
when trying torun VLC from terminal, i got what looked like good results from its txt:
/usr/bin/vlc
VLC media player 2.1.4 Rincewind (revision 2.1.4-0-g2a072be)
[0xc68118] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.

but i only got an icon on the launch bar, and an icon up top right on the black bar.
any ideas what is wrong there?
and still happens with other progs.

---

### Post by Un_Known on 2014-06-12
when trying to run VLC from terminal, i got what looked like good results from its txt:
/usr/bin/vlc
VLC media player 2.1.4 Rincewind (revision 2.1.4-0-g2a072be)
[0xc68118] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.

but i only got an icon on the launch bar, and an icon up top right on the black bar.
any ideas what is wrong there?
and still happens with other progs.

---

### Post by Un_Known on 2014-06-12
> **oldrocker99 said:**
> The Unity desktop has its quirks; you might want a more traditional one. Try this:
```
sudo apt-get install xubuntu-desktop
```

Hit Y when it asks, and let it download and install. Then log out and select "Xubuntu" from the button by your login. Log in and see if you like XCFE (the desktop used in Xubuntu) better.

BRILLIANT!!!!
what a difference! am very very happy with the result of this advice! it is honestly like running a whole fesh new setup! thankyou very kindly for such a short,simple, humble,no-time-wasting suggestion!
as it happens,before i quit using unity,the default desktop, it had gotten so slow, i thought i was on an old infected, overloaded windows device! even slower.
so-

SOLVED!
this problem is fullyfinished!
thank you toall!and especially old rocker99.

---

