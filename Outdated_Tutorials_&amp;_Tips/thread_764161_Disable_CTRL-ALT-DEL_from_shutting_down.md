---
title: "Disable CTRL-ALT-DEL from shutting down"
date: 2008-04-23
forum: Outdated Tutorials &amp; Tips
---

### Post by DBrocks on 2008-04-23
Hey folks. I've been noticing, alot of people have been asking me on how to disable CTFL-ALT-DEL from shutting down their server. So, I've decided to write this short little entry to hopefully solve, once and for all, these questions. So, here we go.

[SIZE=5]Dapper, and earlier
[SIZE=2]1. If you are using Dapper Drake, or before, you will have to edit /etc/inittab with the editor of your choice[/SIZE][/SIZE]. (I prefer nano, I am a command line guy, but feel free to use which ever you want.

```
sudo nano /etc/inittab
```2. Now, look for the line that looks like this:
```
exec /sbin/shutdown -r now "Control-Alt-Delete pressed"
```This is what we want to change. delete whole line. Now, its up to you what you want to do. If you want it to just print a message, and then do nothing, enter this:
```
"CTRL+ALT+DEL is disabled!!"
```or any other message of your choice. 
If you want it to execute a script, change the line to
```
exec /path/to/your/script.sh
```Thats it! Now, you can leave your server in peace, and not have to worry about anyone pressing CTRL+ALT+DELETE, and shutting it down!:lolflag:

[SIZE=5]Edgy, and newer[/SIZE]

In Edgy, you have to edit /etc/event.d/control-alt-delete. Then, just follow the steps in step 2 of Dapper and Earlier.


Thats all! Any suggestions are welcomed!

~Dan

---

