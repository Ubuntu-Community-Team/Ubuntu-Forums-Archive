---
title: "Online Accounts into System Settings"
date: 2011-07-31
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by novatillasku on 2011-07-31
Hi all!.Today install the yesterday's daily build of oneiric.
Gwibber isn't installed.

Into System Settings are now Online Accounts and includes Google accounts.

[IMG]http://novatillasku.com/wp-content/uploads/2011/07/herramientas-personal.png[/IMG]

[IMG]http://novatillasku.com/wp-content/uploads/2011/07/2.png[/IMG]

---

### Post by ELD on 2011-08-01
Hmmm so it says it uses mail, chat, calander etc. But how does it do it, would it auto add a chat account to Empathy, should it add an email account to thunderbird....what's the point of it?

---

### Post by Sennaista on 2011-08-02
What is this supposed to do? I have signed into my Google account but I don't see how things can be taken forward from there or what it is supposed to do really.

It's a new entry under "system settings" in Gnome-Shell.

---

### Post by Harry33 on 2011-08-02
There is already a thread about this:

[http://ubuntuforums.org/showthread.php?t=1815541](http://ubuntuforums.org/showthread.php?t=1815541)

---

### Post by Sennaista on 2011-08-02
> **Harry33 said:**
> There is already a thread about this:

[http://ubuntuforums.org/showthread.php?t=1815541](http://ubuntuforums.org/showthread.php?t=1815541)

Ok, thanks.

---

### Post by Sennaista on 2011-08-02
It's all very cryptic. :confused:

---

### Post by Roo79x on 2011-08-02
I asked the same thing too seems no one who knows what it's about cares enough to give an answer

[http://ubuntuforums.org/showpost.php?p=11100911&postcount=1](http://ubuntuforums.org/showpost.php?p=11100911&postcount=1)

---

### Post by williejones on 2011-08-02
I am up to date with updates and do not have this.

---

### Post by mc4man on 2011-08-03
I would guess it's a tool to be used to add acounts that can be used by some app(s)
for example
[http://afaikblog.wordpress.com/2011/06/09/presenting-gnome-contacts/](http://afaikblog.wordpress.com/2011/06/09/presenting-gnome-contacts/)

> **williejones said:**
> I am up to date with updates and do not have this.
It's possible no amount of updates will add it, though if you do a fresh install w/ the current daily  or A3 next week? it will certainly be there

Otherwise if you copy the .desktop from /usr/share/applications to ~/.local/share/applications it should show up.
gnome-online-accounts-panel.desktop

---

### Post by Harry33 on 2011-08-03
> **williejones said:**
> I am up to date with updates and do not have this.

Gnome-control-center depends on libgoa-1.0-0, which is the gnome online accounts service.
So, do you have the version 3.1.4 installed?

---

### Post by cariboo on 2011-08-03
merged two threads on the same subject.

---

### Post by m.rankovic on 2011-08-03
> **williejones said:**
> I am up to date with updates and do not have this.

On my install Online Accounts and Ubuntu One show in System Settings **ONLY** if I clik on *Power Indicator > Power Settings > All Setting*... Weird...

[http://www.youtube.com/watch?v=JRKEBzpJOnY](http://www.youtube.com/watch?v=JRKEBzpJOnY)

---

### Post by jbicha on 2011-08-03
[https://live.gnome.org/Design/SystemSettings/OnlineAccounts](https://live.gnome.org/Design/SystemSettings/OnlineAccounts)

Basically, it's a one-stop shop so that you only have to enter your login information once and any GNOME app that uses the service will pick up your login info. At the moment, only Google is turned on by default and there are only a few apps supporting it so it's not very useful yet. I think it should work with Thunderbird (if not, that's a bug) but Thunderbird does not have desktop calendar integration yet.

---

