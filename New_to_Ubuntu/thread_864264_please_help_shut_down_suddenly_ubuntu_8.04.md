---
title: "please help shut down suddenly ubuntu 8.04"
date: 2008-07-19
forum: New to Ubuntu
---

### Post by kambeng02 on 2008-07-19
hye to all,
i just upgrade my ubuntu to 8.04 with a few problems and its all has been solved. however, my ubuntu keep shuttig down itself suddenly. i dont know whats the problem. im expecting that the fan didnt work. but i dont know if thats the real problem. how can we find wether the fan is working or not? 

im using v3000 presario notebook adn dual boot ubuntu with vista basic

thanks in advance

---

### Post by Canis familiaris on 2008-07-19
Do you use Desktop or a Notebook?
EDIT: Oh I see you use a notebook. My mistake.

Is the laptop overheating?

---

### Post by baju on 2008-07-19
If the fan is not working the temperature should increase dramatically. Do you have a hardwaremonitor installed?

---

### Post by kambeng02 on 2008-07-19
i've installed hardware monitor, how should i know wether it is overheating or not, the graph seems okay to me, if im not mistaken, lol, anyway, thanks for reply, and please post me any idea why my laptop always shutting down by itself, thanx again

---

### Post by kambeng02 on 2008-07-20
gosh, i still cant solve the problem, anyone can help me?

---

### Post by Portable_Jim on 2008-07-20
Some thoughts:
Does the battery work fine?
Does it happen running the live CD?

---

### Post by makito on 2008-07-20
kambeng02, can you post the output of dmesg, acpi -V and /var/log/acpid?

To do this, open a terminal and type
```
dmesg > dmesg.txt
cat /var/log/acpid > acpid.txt
acpi -V > acpi.txt
```

There should now be three files in your home folder, one called dmesg.txt, one called acpid.txt, and one valled acpi.txt. Post those (as attachments please) and I will look through them. 

Also, can you explain your problem in a little more detail? Is there anything you can do to reproduce the problem, i.e. induce these abnormal shutdowns? Is there anything that stops the problem, are there any other weird things happening when it shuts down? You said you thought it was the fan, what is happening that makes you think that?

---

### Post by kambeng02 on 2008-07-20
here is the file, the ubuntu just shutting down like usual, its like checking all the hardware like at the first time we run the live cd, and then it power off itself, there's some failure note when the checking process at the network, but the wireless seems fine after i boot it back

---

### Post by kambeng02 on 2008-07-20
here the other 2 files, sorry for not include the other one

---

### Post by makito on 2008-07-20
kambeng02

I still don't quite understand what the problem is. Can you please describe exactly what you do, what happens, and what you expected to happen. Paragraphs and capitalization help immensely. I can't help you if I don't understand what the problem is.

please type these lines into the terminal and post the acpitool.txt it creates
```
sudo aptitude install acpitool
acpitool -e > acpitool.txt

```and if you don't want the program acpitool to stay installed on your computer
```
sudo aptitude purge acpitool
```

---

### Post by makito on 2008-07-20
Looking through your logs it looks like you have battery problems. First thing I would try is shutting down the computer and letting it charge for a few days, I noticed that your battery is only 9% charged. It is also possible that you have a loose connection either to the battery or the AC power.
When it shuts down, does it instantly power off, or does it do the normal shutdown routine? Also, does it do this intermittent shutdown both on battery power and AC?

---

### Post by kambeng02 on 2008-07-23
hye makito, 
thanks for the reply, yes i have battery prob, but is it the reason y my ubuntu shutting down suddenly. currently im using ac power only without the battery. besides, the ubuntu shutting down normally, and i think i know what's the prob, my cpu temperature was high, when idle, the temp is about 50-60, and when im running an audio player for 10 minutes, the temperature is about >80 degrees, what should i do? i have no problem running in vista as im dual boot it with vista. thanks again makito

---

### Post by makito on 2008-07-25
Hey Kambeng02
   So it looks like we have narrowed things down to two problems. Either it is the battery or it is the fan. If you could post the ouput of just a few more commands that would be helpful. By the way, how much of the commands I have been asking you to run do you understand? Are you comfortable on the command line or do you want me to keep giving you explicit code to run?

At any time
```
[FONT=monospace]
[/FONT]cp -r /proc/acpi /tmp[FONT=monospace]
[/FONT]tar -cvjf ~/acpi.tar.bz /tmp/acpi

```

post the acpi.tar.bz file it creates

After you have just rebooted from one of your odd shutdowns run the following command and post the kern.log.0 command it creates.
```

cat /var/log/kern.log.0 > kern.log.0
```

Hopefully this will tell us if it is the battery or the fan. Or something else entirely

---

### Post by kambeng02 on 2008-07-25
here is the acpitool.txt file u asked before, sorry for the late, my class has started, about the acpi.tar.bz file, i still have trouble to create it as it give me an error 
> cp: cannot open `/proc/acpi/event' for reading: Device or resource busy


i'll try it again after i reboot it. thanks makito

---

### Post by makito on 2008-07-25
Don't worry about that error, I got the information I needed from the acpitools.txt file.
    From what I can see the issue is your battery, but I want to try one more thing. Try shutting the computer off and leaving it plugged in for a day, then run acpitools again and post the ouput.
```
acpitool -e > acpitool.txt
```

And if you do get the wierd shutdown, boot up and post the /var/log/kern.log.0 file.

---

