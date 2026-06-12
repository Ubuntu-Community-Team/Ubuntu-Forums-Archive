---
title: "Evolution"
date: 2008-09-22
forum: New to Ubuntu
---

### Post by bobigeorge on 2008-09-22
Hello

I am looking for a way to NEW MAIL NOTIFICATION without opening evolution. I am getting new mail notification only when i open evolution. I need to get a mail notification first and then i would like to open evolution to read it.

thanks in advance..

---

### Post by SpenceMakesSense on 2008-09-22
try alltray.... Didnt work well for me but then again I was using thunderbrid instead of evolution but it keeps in the background and in a tray icon on your gnome panel(like pdgin and network connectivity icons)

---

### Post by bobigeorge on 2008-09-23
Thanks SpenceMakesSense

Is there no other way to stay with Evolution and use mail notification. I don't feel like installing another program when I already have one mail reader... Thank u very much

---

### Post by hggdh on 2008-09-23
The problem here is your requirement: New email notification *without* Evolution running. Or, more generically, new mail notification *without* the email client running.

Since it is the mail client that checks for new email, you end up having to be running the client first of all... or installing (and configuring) an "email checker" to do that -- for example, the google email checker.

Some email clients provide a small-footprint email checker to do that; Evolution does not.

Probably the best you can do is indeed run Evolution under alltray, and configure Evolution's Email Notification plugin. This way, Evolution can be minimised on the tray, and you will get a notification when new email arrives.

Hope this helps.

---

### Post by styfle on 2008-09-23
Firefox has an addon that gives you a notification but it only works for popular email addresses such as yahoo, hotmail, gmail, etc.

Thats not exactly what you asked for but its a nice feature
PS I'm not sure if this actually works with linux seeing as I have this addon for my windows machine

---

### Post by iansane on 2008-09-23
To keep from going back to the menu twice, once for evolution and then again for alltry and then clicking on the window to dock,

```

alltray evolution

```

in terminal will run evolution docked all in one command.

That can be easily made into a new evolution launcher.

As far as automatically send/recieve at start up, I'm wondering if a shell script can open evolution and then send the "F9" command? If so it could open, dock, and send/recieve with one launcher. Anyone know how to send that command to evolution in a script?

Put it together with the above command and there it is.

---

### Post by bobigeorge on 2008-09-24
Thank you all for the help. 

I think.. I will try alltray...and I would like to know more about the 'shell script'

---

### Post by iansane on 2008-09-24
I want to know more too. I was hoping someone with mad scripting ninja skills would write it up and post it. LOL

I'm trying to figure out how to say "F9" to evolution through terminal or a script. All I can find are xml files in evolution folder that tell it what shortcut to use but I don't know the actual system command or how to tell it the keyboard signal.

---

### Post by rosswmcgee on 2008-09-24
I have mail notification on my sys tray, it indicates when there is mail, and allows you to see what has arrived with out opening Evolution. I will see if any of my old posts say how to do it, but off hand I think
you can go to synaptic manager and find it there. It will then appear in 
applications under internet, and from there to your sys tray.

---

### Post by rosswmcgee on 2008-09-24
OK, it is in in synaptic manager. Just search mail notification, and install mail notification in system tray. You will have an easy way to see what you want without having to open Evolution.

---

### Post by iansane on 2008-09-25
looks like more trouble than it's worth to me. evolution can notify and it can be minimized or use alltry in the evolution command as I said above. "alltray evolution" opens and docs it all in one command.

the mail notifier's ssl/tls options are greyed out and that's what I have to have to connect to gmail. Also the notifier is invisible till it finally starts flashing the error cause it could not connect with the settings available.

I just thaught it would be good to have it send and recieve on start up instead of waiting for the notifier.

yep just did it. only problem is it checks every minute if I want to check within a minute of startup.

Surely a script to run "alltray evolution (command to send/recieve)" would make more sense than installing another app that has to be set up with log in info to do it.

Oh well, no big deal, just got interested and wanted to find out about it when I saw this post.

---

### Post by iansane on 2008-09-25
yeah that's not good in my opinion. I figured out the gmail setup and now when I get new mail the open option opens browser to gmail login instead of opening it in evolution.

It's not even integrated into evolution.

So I don't think it should be called evolution-email-notifier.

It's just another application.

Good app and it's fine for some, but I'm gonna try to figure out another way to just make evolution send/recieve at start up if it's possible.

bobigeorge, let us know if you find anything since you liked the idea of the script.

---

### Post by hggdh on 2008-09-25
Did you configure the Evolution mail notification plugin Edit/Plugins/Mail Notification)?

---

### Post by iansane on 2008-09-25
OK I appolagize. My mistake.

Now it is send/recieving at startup. So changing the launcher to "alltray evolution" does work since the mail-notifier is installed. Even with "check for mail" in the account settings set to 5 min.'s it still send/recieve at start up.

However just starting evolution-mail-notifier without evolution running would only open browser page instead of evolution so I don't even need a launcher for the notifier in my menu. 

Hope this was helpful to the OP. I know my problem is solved now. No need for a script.

---

### Post by Vamp898 on 2010-09-23
alternative you can install for example "evolutoin-statusicon"

install that and Evolution will showup in tray =)

there is also an second plugin which can do that

---

### Post by Chad Olson on 2010-09-23
I use gmail notifier from the software sources there are many there that may work for you

---

