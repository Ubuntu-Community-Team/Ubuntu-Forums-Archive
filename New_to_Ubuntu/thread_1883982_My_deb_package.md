---
title: "My deb package"
date: 2011-11-20
forum: New to Ubuntu
---

### Post by redpower1989 on 2011-11-20
[FONT=Arial Black]Hello 
I make my deb package.
I can install it with software center ubuntu but can't install it with command 
sudo apt-get install name.deb .

How can i fix it?
[/FONT]

---

### Post by themusicalduck on 2011-11-20
You can install a .deb from the command line with

```
sudo dpkg -i package.deb
```

---

### Post by redpower1989 on 2011-11-20
thanks for the new command.But the problem is'n fix.
Do you think that exist problem in the package?Maybe i must do something to my package and after that it can install with command?

> **themusicalduck said:**
> You can install a .deb from the command line with

```
sudo dpkg -i package.deb
```

---

### Post by gandaran on 2011-11-20
> **redpower1989 said:**
> [FONT=Arial Black]Hello 
I make my deb package.
I can install it with software center ubuntu but can't install it with command 
sudo apt-get install name.deb .

How can i fix it?
[/FONT]
you can only install packages with 'apt-get install' command from repositories on software sources.
you would have to create your own repository and add it to software sources.

---

### Post by redpower1989 on 2011-11-20
Thanks!!:D
 i search for it !

> **gandaran said:**
> you can only install packages with 'apt-get install' command from repositories on software sources.
you would have to create your own repository and add it to software sources.

---

### Post by Jacobonbuntu on 2011-11-20
> **redpower1989 said:**
> Thanks!!:D
 i search for it !


I am not sure you precisely understand the post from the musicalduck :)
when he says: "sudo dpkg -i package.deb", "package.deb" should be replaced with the (exact) name of the actual package you are installing, preceded by its location. 

for example: if you want to install "Dropbox.deb", located in your "Downloads" folder, your command would be: 
sudo dpkg -i /home/your-name/Downloads/Dropbox.deb

---

### Post by redpower1989 on 2011-11-20
I already know that.That's obvious. thanks for your interest:) 


> **Jacobonbuntu said:**
> I am not sure you precisely understand the post from the musicalduck :)
when he says: "sudo dpkg -i package.deb", "package.deb" should be replaced with the (exact) name of the actual package you are installing, preceded by its location. 

for example: if you want to install "Dropbox.deb", located in your "Downloads" folder, your command would be: 
sudo dpkg -i /home/your-name/Downloads/Dropbox.deb

---

### Post by Jacobonbuntu on 2011-11-20
> **redpower1989 said:**
> I already know that.That's obvious. thanks for your interest:)

....sorry if I underestimated you :) , it is sometimes hard to tell what someones experience is...

---

### Post by redpower1989 on 2011-11-20
Don't worry. We must tell some things! You did very well!

> **Jacobonbuntu said:**
> ....sorry if I underestimated you :) , it is sometimes hard to tell what someones experience is...

---

