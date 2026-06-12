---
title: "No email notifications in Ubuntu messaging menu"
date: 2012-04-22
forum: New to Ubuntu
---

### Post by kadama on 2012-04-22
Hi everyone,

I am using Ubuntu 12.04 with Unity and I have linked Thunderbird to my Gmail account. When I receive an email I don't get any notifications in the messaging menu. I have heard that the small white envelope turns blue or green when a new email has arrived, but not for me. 

I click on the white envelope, Thunderbird starts downloading the emails and only then the white envelop turns blue, I hear a short sound and I get a pop up window saying that I have a new email. But that's kind of late, isn't it? I would like to receive all this notifications before opening Thunderbird. A very reasonable thing to ask. 

Does it work for the rest of you? Any ideas for fixing it?

---

### Post by Baldrick_NZ on 2012-04-22
> **kadama said:**
> Hi everyone,

I am using Ubuntu 12.04 with Unity and I have linked Thunderbird to my Gmail account. When I receive an email I don't get any notifications in the messaging menu. I have heard that the small white envelope turns blue or green when a new email has arrived, but not for me. 

I click on the white envelope, Thunderbird starts downloading the emails and only then the white envelop turns blue, I hear a short sound and I get a pop up window saying that I have a new email. But that's kind of late, isn't it? I would like to receive all this notifications before opening Thunderbird. A very reasonable thing to ask. 

Does it work for the rest of you? Any ideas for fixing it?

Hi Kadama,

The white envelope turns blue, but only when you have Thunderbird open or minimised and you get a new message. It works through your email client, rather than a direct connection with gmail.

Hope this helps.

---

### Post by audiomick on 2012-04-22
> **Baldrick_NZ said:**
> It works through your email client,

I'm not sure about this, I use Evolution, not Thunderbird. However, I believe the choosing the option for a visual notification in Evolution is what causes the Envelope to turn blue. Have a look in you Thunderbird preferences and see if you can see anything there.

---

### Post by kadama on 2012-04-22
Hi again,

the settings seem to be fine and they do work, but only if Thunderbird is already running.

thanks for the suggestion though

[Baldrick_NZ]("http://ubuntuforums.org/member.php?u=708099") you are probably right. But if it is true than it's not very useful. The only benefit would be to manage multiple email accounts. Thanks for replying

---

### Post by neo1691 on 2012-06-11
Anyway to start thunderbird when ubuntu starts??

---

### Post by bencouve on 2012-06-11
You should be able to start thunderbird by entering a script in the rc files

---

### Post by deadflowr on 2012-06-11
> **neo1691 said:**
> Anyway to start thunderbird when ubuntu starts??

Just add thunderbird to the startup applications.
Click the cog at the top right, go down to startup applications, open, click add, give it a name, the command is thunderbird(easy peasy), set or don't set a comment, click ok, or whatever it is, exit.Next time you log in thunderbird will launch automatically.
Expect it to add some time to loading your desktop, as thunderbird is a big program to launch.

---

### Post by neo1691 on 2012-06-11
> **deadflowr said:**
> Just add thunderbird to the startup applications.
Click the cog at the top right, go down to startup applications, open, click add, give it a name, the command is thunderbird(easy peasy), set or don't set a comment, click ok, or whatever it is, exit.Next time you log in thunderbird will launch automatically.
Expect it to add some time to loading your desktop, as thunderbird is a big program to launch.
Thanks, how do you people get the commands so easily?? It seems like a mystery to me

---

### Post by bencouve on 2012-06-11
That was a great tip, thanks deadflower. My old school method is well out of date !  Just learning how far linux has moved on...

---

### Post by neo1691 on 2012-06-12
Okay cool but guys, how can i start thunderbird in background?? Any options??

---

### Post by bencouve on 2012-06-12
[neo1691]("http://ubuntuforums.org/member.php?u=1291990") you should be able to do this from the rc (run control) scripts, as I mentioned earlier. 

Look under /etc/rc0.d - rc6.d

These folders hold the scripts for starting processes during boot. If you want it running in the background then it would be a

./thunderbird &

kind of script

The solution provided previously will start thunderbird but not in the background

---

### Post by deadflowr on 2012-06-12
> **neo1691 said:**
> Thanks, how do you people get the commands so easily?? It seems like a mystery to me

You can look in the folder /usr/share/applications. inside will be all the programs you have installed. Find your program of choice and right-click->properties, it will list the program name and then the command. Most commands will be long and robust, like /usr/bin/gnome-system-monitor, but some are very simple, like nautilus, or thunderbird. It'll probably list it as something like nautilus %U, but you only need to type nautilus to launch it. Being that these are commands, you can launch them from the terminal, like when you launch gedit.(by the way, /usr/bin/programname isn't actually the command, but rather a link to the executing command. I use this as it can be easier to launch a program then to type out sometimes rather long command names)

---

### Post by neo1691 on 2012-06-12
Thanks a lot guys !!

---

### Post by neo1691 on 2012-06-21
But folks, even after running thnnderbird when the system starts, there are no new mail notifications.. How do i get the notifications back??

---

