---
title: "How to handle command 1 &amp;&amp; command 2 in bash script"
date: 2014-10-18
forum: New to Ubuntu
---

### Post by Evan I S on 2014-10-18
Hi Geeks!

I am trying to create .sh file with below commands.  It works perfectly on terminal.  But it does not work with in sh format.  I found that it created multiple of folders which supposed to be only one.  Thus I am susupicous on the symbol && may not handled properly.  Any one has idea?  I appreciate you reply!  Thank you! (I trid without double space and carriage return line feed)


&#8203;[FONT=trebuchet ms]&#8203;mkdir /home/evn/Dropbox/prac2/$(date +"%d_%b|%H:%M:%S") &&  
cd /home/evn/Dropbox/prac2 && 
declare "mm=$(ls -Art | tail -n  1)" && 
var="mm" && 
echo "${mm}" && 
cp  /home/evn/seldoing/* /home/evn/Dropbox/prac2/"${mm}"

[/FONT]

---

### Post by Lars Noodén on 2014-10-18
When you split a line, you have to end the sections with a backslash.  That's probably what's missing from your script.

```

[****code]
&#8203;mkdir /home/evn/Dropbox/prac2/$(date +"%d_%b|%H:%M:%S") && **\**
cd /home/evn/Dropbox/prac2 && **\**
etc...
[/****code]

```

---

### Post by matt_symes on 2014-10-18
Hi

> **Evan I S said:**
> Hi Geeks!

I am trying to create .sh file with below commands.  It works perfectly on terminal.  But it does not work with in sh format.  I found that it created multiple of folders which supposed to be only one.  Thus I am susupicous on the symbol && may not handled properly.  Any one has idea?  I appreciate you reply!  Thank you! (I trid without double space and carriage return line feed)


&#8203;[FONT=trebuchet ms]&#8203;mkdir /home/evn/Dropbox/prac2/$(date +"%d_%b|%H:%M:%S") &&  
cd /home/evn/Dropbox/prac2 && 
declare "mm=$(ls -Art | tail -n  1)" && 
var="mm" && 
echo "${mm}" && 
cp  /home/evn/seldoing/* /home/evn/Dropbox/prac2/"${mm}"

[/FONT]

You may find it easier to do something like this.

```

db_dir=/home/evn/Dropbox/prac2/$(date +"%d_%b|%H:%M:%S") && \
mkdir "$db_dir" && \
cp /home/evn/seldoing/* "$db_dir";
```

Kind regards

---

### Post by Evan I S on 2014-10-19
Hi Lars!

Thank you for your help. You are right after adding \ does not create multiple folders but I banged with other issue that declare: not found. ouch

Hi matt_symes!

Thank you for your hlep.  I learned from you how can my script be concise.

---

### Post by steeldriver on 2014-10-19
How exactly are you trying to run the script? A common mistake is to try to run a bash script using 

```

sh somescript.sh

```

which (on current versions of Ubuntu) actually uses the **dash** interpreter (which doesn't have the [FONT=courier new]declare[/FONT] keyword) rather than the **bash** interpreter.

---

### Post by Evan I S on 2014-10-19
Hi steeldriver

Oh you are right! I tried with sh command.  It works fine with ./ instead thank you for your help!!!  If you would not mind could you please look at another issue on 

Run 

'sudo chmod 777 /sys/class/leds/smc::kbd_backlight/brightness && echo 0 | tee -a /sys/class/leds/smc::kbd_backlight/brightness' 

commands at startup without requiring sudo passwd.  in my sudo visudo I commented as follows

evn ALL=(ALL) NOPASSWD: /sys/class/leds/smc\:\:kbd_backlight/brightness
evn ALL=(ALL) NOPASSWD: /sys/class/leds/smc\:\:kbd_backlight/[COLOR=#980101][B]

Waking from sleep mode lights back thus I need to perform the same commands above again and again.  I dont mind permanently disable it If I can do :-)


You could post your answer to another thread ---->  [ubuntu][/B][/COLOR]  [Permanently turns off MacbookAir 2011 Mid Keyboard backlit  14.04]("http://ubuntuforums.org/showthread.php?t=2248568&p=13144214#post13144214")

---

