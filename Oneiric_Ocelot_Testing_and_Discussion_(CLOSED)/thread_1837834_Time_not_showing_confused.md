---
title: "Time not showing :confused:"
date: 2011-09-02
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by tungmeister on 2011-09-02
Hi guys, Just installed the beta and everything is working apart from the software center and the system time, I can live without the software center as I prefer using synaptic anyway but I can't without the system time showing. Instead of the actual time being displayed the string "Time" is shown in the notification area. Anyone any Ideas?

---

### Post by cariboo on 2011-09-02
Start dconf-editor, you need to have dconf-tools installed, then go to com->canonical->indicator->datetime.

See the screenshot

---

### Post by tungmeister on 2011-09-02
> **cariboo907 said:**
> Start dconf-editor, you need to have dconf-tools installed, then go to com->canonical->indicator->datetime.

See the screenshot

I don't have any options to change under datetime in the dconf-editor:
[IMG]http://i191.photobucket.com/albums/z189/tungmeister/Screenshot20at202011-09-0320013A093A37.png[/IMG]

EDIT: I've got the options visible now it was just the window being buggy not showing. I've got the same check boxes and time format as you already.

---

### Post by lucazade on 2011-09-02
dconf-editor is quite bugged, click under the column Name and use the arrow keys to go down. you'll see the right pane expanding and showing available options.

---

### Post by tungmeister on 2011-09-02
> **lucazade said:**
> dconf-editor is quite bugged, click under the column Name and use the arrow keys to go down. you'll see the right pane expanding and showing available options.

Ye I've worked it out and got the options to show, They all appear to be set correctly as shown in cariboo907s post. Any further suggestions, it's sooo annoying not having the time shown.

---

### Post by cariboo on 2011-09-02
Have you tried unticking Show-clock, closing dconf-editor, then opening it again and enabling show-clock?

---

### Post by tungmeister on 2011-09-03
Yes, It made no difference though.

---

