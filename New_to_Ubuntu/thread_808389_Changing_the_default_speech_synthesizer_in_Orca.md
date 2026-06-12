---
title: "Changing the default speech synthesizer in Orca?"
date: 2008-05-26
forum: New to Ubuntu
---

### Post by Mikey_33 on 2008-05-26
Hello,

     I just installed Ubuntu, and everything is great so far.  The problem I am having is trying to setup and configure Orca to my satisfaction.  I currently use Windows XP with a program called Zoomtext.  At first glance, Orca seems to be the best alternative for the Linux system.  I should also mention that I am very new to the Linux world.  Here is the problem I am having:

     I can't understanmd half the words that  are spoken from the default speech synthesizer that Orca uses.  In order for me to continue using Linux, I need to change this speech synthesizer to a more naturally sounding voice.  One option is to purchase one from [http://www.cepstral.com/](http://www.cepstral.com/).  I read somewhere that cepstral voices will work with Orca.  I think I also read somewhere that it needs to use Speech Dispatvher, which I did install.  However, it is not showing up in Orca.  

     I would appreciate it very much if someone could help me change the robotic voice of Orca, to one that I can understand better.  It does not necessarily have to be a voice from cepstral.  I am open to options, especially easy ones.  It seems like every web site I find, always gives instrustions in command line form, as opposed to GUI instrustions.  I don't mind the command interface, because I come from the old DOS days.  But it is very frustrating when trying to learn something totally different.  

     I also tried installing a demo version of one of the voices from cepstral.  Halway through, the terminal closed out without giving me any indication that it was completed.  I even tried going to the folder where it should have installed it to, and there was nothing there.  So, I am very frustrated and confused.  Other than that, I am very happy with Ubuntu.

     I tried all day yesterday with no success.  So, I thank you all in advance if you could give me a step by step procedure on how to change speech synthesizers in Orca. Or, even providing me with an apternative prgram that is equvalent to Orca.  I don't care what the solution is; it just has to include the end result of having a more human sounding voice.


Thanks,
Michael

P.S.  I prefer the KDE desktop, and was thinking about installing Kubuntu instead.  If I did that, would I still be able to use Orca, or some other equivalent of it?

---

### Post by Mikey_33 on 2008-05-26
Hi,

     I just realized that there is a special area for posts regarding asistive technology and accessibility.  I am sorry that I posted this here.  As you can tell, I am new to this forum.  I hope there was no harm done.

Please disregard this thread because I am going to copy and paste it over to the proper section.  Hopefully a board admin can go ahead and delete this thread because I was not able to find a way to delete it myself.  

     I am just so frustrated right now.  In my fit of frustration, I just deleted Linux off my computer.  I hope this is only a temporary action on my part.  It's hard enough to learn something new.  It is even more challenging being legally blind as well.  

     Again,  I am sorry.  Hopefully I will get some replies when I copy it into the proper area of the forum.  

Michael

---

### Post by mj86 on 2008-05-28
i think i can help you
try festival
sudo apt-get install festival festvox-kallpc16k
and for cepstral you only need gnome-speech-swift
if you have more questions i can ofcourse help you

---

### Post by Mikey_33 on 2008-05-29
Hi mj85,

     Thank you for your help.  I installed the Festival speech synthesizer by copying the command you gave me.  It worked as far as showing up in orca.  However, I have a very mysterious problem right now.  When I change to Festival in orca, I lose my magnification.  The voice does change to Festival.  

I tried rebooting the computer, but no luck.  Upon rebooting, orca runs, but the magnification is not working.  I go into preferences and I still see that all my magnification settings are the same, and it is enabled. I try setting the synthesizer back to its default, and the magnification comes back.

Also, even before I began to tinker around with oca, I would always have to reboot every time I changed a setting.  When I change a setting and click apply, orca restarts itself, but I lose the magnification.  When I reboot, the magnification comes back.  Do you know why the magnification fails to return when I apply  any changes?  The magnification does show for a split second when I either click the apply for new changes, or when I click the restart button.  Then, on reboot, everything is fine.  However, as I mentioned, when I use Festival, I am not able to get any magnification, even on a reboot.

I tried your second suggestion to install the driver for Cepstral voices.  After I did that, nothing really happened.  It does not show up in orca.  Also, when I try installing a demo Cepstral voice, the terminal closes when it gets to the step of creating the directory.  It says  the directory does not exist, so I type in the default one that it suggested and hit enter.  Then terminal closes without installing my Cepstral voice.

Festival is actually alright, so I can live using that synthesizer.  I can understand it better than the default.  But, I would like to be able to use Cepstral voices too.  

Just so I did not confuse you, I will summarize my problems. 

1. Festival works but I lose magnification, even on rebooting, but it does come on for a split second after clicking the apply, or reboot buttons.  I change back to the default synthesizer and the magnification works.

2. Whenever I change a setting in Orca, the program restarts with the new settings.  However, the magnification only comes back for a split second and shuts off.  The program is still running when this occurs.  A reboot, or re-login brings it back.  This is really frustrating.

3.  After installing the swift driver you suggested,, nothing shows up in orca for that synthesizer.  When I try installing a Cepstral voice, the terminal setup closes right after the step of creating the directory for the voice.  I then go to the folder with file manager and the directory was not created.

I hope I provided enough detail without any confusion.  I would be very happy if I could just get the magnifier to work with Festival.  Getting Cepstral voices to work would be an extra.  

I really do appreciate any and all help you give me.  

Thaks,
Michael

---

### Post by mj86 on 2008-05-29
i not use magnification sorry
to use cepstral create a file  caled swift.conf in
/etc/ld.so.conf.d
with the following
/opt/swift/lib
also try to use the standard terminal by press ctrl+alt+f1

---

### Post by Mikey_33 on 2008-05-29
I don't know how to use terminal commands yet.  

I tried using the file manager but it wont let me create a file in that folder.  I assume it has to do with permissions of working with system files and folders.  Do you know how I can change the permissions on my login name to make that file?

I created the file in desktop.  Could you tell me the command to use to copy it to the proper folder, using terminal?

Are there any other free voice systhesizers that I could try besides Festival?  If so, can you tell me some and how to install them?  


Thanks,

Michael

---

### Post by mj86 on 2008-05-30
you must do the file in the terminal
when you are in the terminal
cd /etc/ld.so.conf.d
nano swift.conf
when enter the text i writed

---

### Post by wx1gdave on 2008-12-10
Thanks for the suggestion of Festival and KAL16.  May try that, as I have some delays and stuttering with the default Espeak.

---

### Post by leptone55 on 2013-02-24
Hello,

mj86 i followed your advice and installed festival. I tested it in terminal and the voice is much better!

But festival doesn't show as an option in "Speech synthesizer" in Orca Preferences "Voice" tab. How do I get Orca to use the festival synthesizer?

Thank you!

---

### Post by oldos2er on 2013-02-24
Please start a new thread.

If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

