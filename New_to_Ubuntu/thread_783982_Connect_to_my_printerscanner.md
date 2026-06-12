---
title: "Connect to my printer/scanner"
date: 2008-05-06
forum: New to Ubuntu
---

### Post by GoCool on 2008-05-06
I am not sure if I am framing my question right, so if it sounds confusing please bear with me.
> 
Background:
I have this professional printer cum scanner from Konica Minolta (BIZHUB C250). I could configure the printer, but the scanner is funny, for it gives me too many options and I am still getting used to it. I opted for the easy way and that is to have it scanned to its local hard disk (yes it has its own hdd).


> In M$:
Normally using windows it gives me a s/w called "Page Scope Operator" through which I can access its hdd and copy and paste it to my local hdd.


> My Question
The question is how do I do the same in ubuntu. I have its ip address (the ip of the scanner) and it requires authentication to get in. I can get into the scanner using its own console and get the details like ip address and port details. So how do I get into that server and get the contents which I scanned. It stores the scanned documents in pdf format (it does give me other options too, but this is the default)

---

### Post by mlentink on 2008-05-06
Do you have any idea how that scanner actually talks to windows? Does it use windows-networking? Does it use a webbrowser? 
If it allows you to see and copy those pdf's it must use some sort of file-sharing.

---

### Post by GoCool on 2008-05-06
> **mlentink said:**
> Do you have any idea how that scanner actually talks to windows? Does it use windows-networking? Does it use a webbrowser? 
If it allows you to see and copy those pdf's it must use some sort of file-sharing.

No. I have no clue how its doing. But I am having a faint feeling that the Scanner itself is running on Linux (but that could be just my feeling, no concrete proof). In windows it gives me an interface called "Page Scope Operator" which will allow me to connect to the scanner and it will show me the available boxes in there (when I say box it is the folder/directory which I create using the console which the scanner provides). Hope it helps.

---

### Post by mlentink on 2008-05-06
OK. Let's try this: do you know the IP-address of that scanner?
In Windows you can often find that IP adres by searching for the printers port (the IP-adress will most likely be the same for printer and scanner).

---

### Post by GoCool on 2008-05-06
> OK. Let's try this: do you know the IP-address of that scanner?


The scanner itself has its own console through which I got it. Next what should I do?

---

### Post by mlentink on 2008-05-06
Sorry, should've seen > I have its ip address (the ip of the scanner) and it requires authentication to get in

what happens when you do
```
ssh ip.address.of.scanner
```

or, in a browser:
```
http://ip.address.of.scanner
```

It's highly doubtful that scanner will support ssh, but since you said it needed authentication....

---

### Post by GoCool on 2008-05-06
```
ssh ip.address.of.scanner
```

This is giving me the following error


> ssh: connect to host ip.address.of.scanner port 22: Connection refused

But the browser looks promising

```
http://ip.address.of.scanner
```


This is actually taking me to its web interface page. The first page asks for my password and after entering it, it shows me all the options which I have using its console.

And thank you for responding immediately, I was in office and couldn't check the updates.

---

### Post by GoCool on 2008-05-06
...continuing from above....

I see a scan option in there which is asking for the following

> Host Address
Can I give my computer ip address here?

> File Path
Can I give my computer path here say 
/home/user/ScannedDocuments

> User ID
Is this my computer username?

> Password
Is this my computer password?

> anonymous (by default it's off)
I think it's doing an ftp to my computer, so should I leave it as off?

> PASV mode (by default it's off)
I think it's doing a passive ftp, what should I give here?

> Proxy (by default it's off)
I think ubuntu by default doesnt install any proxy, but I do have a firewall. So any suggestions here?

> Port No (by default it's 21)
I think I should leave it as 21

---

### Post by GoCool on 2008-05-07
And again...the above post is what I am seeing in the web interface when I gave the ipaddress of the scanner in the browser.

---

### Post by GoCool on 2008-05-08
Any help with this one???

---

### Post by GoCool on 2008-05-08
Any help on this one...this was so close to be resolved...and now I am feeling kind of lost.

---

### Post by mlentink on 2008-05-09
> **GoCool said:**
> ...continuing from above....
I see a scan option in there which is asking for the following
Can I give my computer ip address here?
Can I give my computer path here say 
/home/user/ScannedDocuments
Is this my computer username?
Is this my computer password?
I think it's doing an ftp to my computer, so should I leave it as off?
I think it's doing a passive ftp, what should I give here?
I think ubuntu by default doesnt install any proxy, but I do have a firewall. So any suggestions here?
I think I should leave it as 21

Ok...thinking loud here...
First of all, your scanner does at least have a web interface, which should help. Now we need to figure out how to use it.

Before I go out and potentially help you screw up your scanners' connection to the windows-boxes as well...Perhaps you could tell us a bit more about what menu/options that web-interface actually gives you? Could you describe it in a bit more detail?

I ask this because the questions it asks can go both ways: it can act as a client, but also as a server. In view of the fact that you told us this is a professional machine, I think I agree that it allows you to download files to your own machine, i.e. it acts as a ftp-server.
If that is true, then yes, give it your hostname, then give it the path where you wnat the files stored (please make sure the path does exist!) and then your user credentials.
Yes, used anonymous ftp (the chances are slim you exist as a user on that machine, and yes do use PASV (passive transfer mode), no proxy and port 21.

But first: let's make a bit more sure we are correct, so anything you can post about that web-interface is welcome!

---

### Post by rburkartjo on 2008-05-09
go- try installing xsane image scanner. you can get it from applications/add/remove .type in xsane in search box and install. worth a shot/cheesemaker

---

