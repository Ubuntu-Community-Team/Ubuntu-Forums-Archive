---
title: "help with the c# glade# monodevelop thing"
date: 2006-11-03
forum: Programming Talk
---

### Post by Choad on 2006-11-03
[[IMG]http://img145.imageshack.us/img145/649/screenshot2ut4.th.png[/IMG]](http://img145.imageshack.us/my.php?image=screenshot2ut4.png)

i started up with the sample glade# project, that compiled fine. then i replaced the glade resource with my own glade file, and it didnt work.... but i figured out why, i had 2 callbacks for the buttons that werent being handled. so i deleted those events, and it compiled fine, but gave me a warning that the window delete event was never used. so i added a window delete event u can see in the screenshot, but it makes my project not compile. any help?

---

### Post by skeeterbug on 2006-11-03
Your callback must be named exactly the same.

Here is a callback in my GTK# app:
```
private void on_window1_delete_event(object o, DeleteEventArgs args) 
		{
			Application.Quit();
			args.RetVal = true;
		}
```


Here is the XML the glade editor generated:
```
<signal name="delete_event" handler="on_window1_delete_event" last_modification_time="Thu, 10 Aug 2006 18:12:07 GMT"/>
```

Hope that helps!

---

### Post by Choad on 2006-11-06
thanks! makes sense now lol

---

