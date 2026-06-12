---
title: "How do I select a program to open a file"
date: 2008-05-16
forum: New to Ubuntu
---

### Post by nirpius on 2008-05-16
Hi,

Just a quickie here. I've been using Ubuntu a bit but I've always had the same little problem. When I want to open a file with a different program than the ones Ubuntu usually guesses I want, I can never find where the launch file is. I had a look in / and there's loads of impenetrable looking stuff like usr share etc and that kind of thing. Where do I look to find the file that associates with whatevr program it is I am trying to get to open my file?

Thanks

---

### Post by drs305 on 2008-05-16
> **nirpius said:**
> Hi,
Where do I look to find the file that associates with whatevr program it is I am trying to get to open my file?

Thanks

You can run the following. The run commands are often in the /bin, /sbin, or /usr/bin folder and are usually the name of the app.
```
whereis app_name
```

In nautilus, you can right click on a file and select Properties, Open With and ubuntu will have figured out some of the apps that can run it.

Here is what I get when I type 'whereis gimp'. Notice the /usr/bin/gimp entry, which is a good indication that 'gimp' is a proper command to open it.

```

~: whereis gimp
gimp: /usr/bin/gimp /etc/gimp /usr/lib/gimp /usr/lib64/gimp /usr/share/gimp /usr/share/man/man1/gimp.1.gz

```

You can also see the files list in synaptic by selecting Properties, Installed Files.

---

### Post by nirpius on 2008-05-16
> **drs305 said:**
> You can run the following. The run command is usually in the bin or sbin folder.
```
whereis app_name
```

But if I don't know the name of the app (or at least what it's command name is - aren't some things listed as diffificult to guess things like ffox instead of firefox etc.) Isn't there a folder where most of this stuff is usually kept? e.g. like in Window's Program Files folder.

---

### Post by nirpius on 2008-05-16
That seems to do the trick- sos I can just look in the binary folder? under usr? Cheers

---

### Post by drs305 on 2008-05-16
You are correct, and I don't have a good answer. An example is RealPlayer. The command is realplay. If you typed 'whereis realplayer' you wouldn't find it.

---

