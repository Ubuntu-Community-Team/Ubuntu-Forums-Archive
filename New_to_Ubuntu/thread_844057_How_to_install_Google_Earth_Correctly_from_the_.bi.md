---
title: "How to install Google Earth Correctly from the .bin?"
date: 2008-06-29
forum: New to Ubuntu
---

### Post by Fatfool on 2008-06-29
good day.

I wish to ask the question about installing google earth in a correct manner after downloading the file from the google's webbie. I wish to do this without the repository this time so as to learn about the command line.

I have tried ```
chmod +x GoogleEarthLinux.bin

sudo ./GoogleEarthLinux.bin
```


but I get the problem where google earth run from the applications--> internet menu or through the line 'googleearth' only shows a starfield and the line 'sudo googleearth' must be used to get it to run as per normal. I googled and found this problem on this thread:
[http://www.nabble.com/Google-Earth-only-works-as-%22sudo%22-td17358682.html](http://www.nabble.com/Google-Earth-only-works-as-%22sudo%22-td17358682.html)

the lines
```
sudo chown $USER:users ~/.googleearth -R
sudo chown $USER:users ~/.local -R
```

which were recommended failed to work. I have since uninstalled google earth with these lines:

```
sudo su -
cd /opt/google-earth/
export DISPLAY=:0
./uninstall
```

as such, I would like to know how to run the installer correctly this time.

---

### Post by paul101 on 2008-06-29
this will install google earth :)


```
wget http://dl.google.com/earth/client/current/GoogleEarthLinux.bin ; chmod +x GoogleEarthLinux.bin ; sudo ./GoogleEarthLinux.bin
```





:popcorn:

---

### Post by tubbygweilo on 2008-06-29
The must use "sudo" to run Google Earth problem can be overcome by browsing this [GoogleEarth Community doc]("https://help.ubuntu.com/community/GoogleEarth")
> 
7 When installation is complete, press Quit.
Do not press Start as this will run it as root which is never a good idea.

---

### Post by hyper_ch on 2008-06-29
instead of installing the binary you should use repos.... if you want to learn how to install programs without the repos, then you should rather use a program that you can compile from source and not one that is distributed as binary installer.

---

### Post by brunolabs on 2008-06-29
I used the binary installer without "sudo" and it worked.

---

### Post by Fatfool on 2008-06-29
> **hyper_ch said:**
> instead of installing the binary you should use repos.... if you want to learn how to install programs without the repos, then you should rather use a program that you can compile from source and not one that is distributed as binary installer.
so long as it isn't pointing and double clicking an excecutable to start the installation, its learning something right?

it still does take a bit of practice to get used to these binary installations for me....

I'll get to the compiling portion in the future but for now i'll have to learn how to use .deb and .bin ones first :)

---

### Post by Fatfool on 2008-06-29
> **paul101 said:**
> this will install google earth :)


```
wget http://dl.google.com/earth/client/current/GoogleEarthLinux.bin ; chmod +x GoogleEarthLinux.bin ; sudo ./GoogleEarthLinux.bin
```





:popcorn:
(erm yeah I actually used those lines)

but yeah as tubby said I guess I gotta use em again. and then press 'Quit'. Wonder why the even have the option to start it and screw with the permissions.

btw i tried 'sh ./GoogleEarthLinux.bin' and it installed into another directory but still had the same problem...

---

### Post by hyper_ch on 2008-06-29
> **Fatfool said:**
> so long as it isn't pointing and double clicking an excecutable to start the installation, its learning something right?

it still does take a bit of practice to get used to these binary installations for me....

I'll get to the compiling portion in the future but for now i'll have to learn how to use .deb and .bin ones first :)

double-clicking an .exe in windows and installing a binary in windows is the same thing basically ;)

---

### Post by Fatfool on 2008-06-30
> **tubbygweilo said:**
> The must use "sudo" to run Google Earth problem can be overcome by browsing this [GoogleEarth Community doc]("https://help.ubuntu.com/community/GoogleEarth")
Ok I just tried this and it doesn't work.

same problem as before. and I don't have the Icon in the Applications --> internet menu as well. (I could make one but no point currently)

using 'googleearth' doesn't work while 'sudo googleearth works'

---

### Post by Fatfool on 2008-06-30
> **hyper_ch said:**
> double-clicking an .exe in windows and installing a binary in windows is the same thing basically ;)
well you still have to chmod +x it :)

closest would be .deb i guess.

---

### Post by hyper_ch on 2008-06-30
.deb is also a binary like an .exe ;)

---

### Post by Fatfool on 2008-06-30
> **hyper_ch said:**
> .deb is also a binary like an .exe ;)
ok ok.... errr lemme get Google earth to work without the sudo command before I get to compiling ok? :)

---

### Post by Fatfool on 2008-06-30
erm anyone figured out why its not acting the same as the first install?

---

### Post by Fatfool on 2008-07-01
more info needed? need me to run any lines?

---

### Post by Fatfool on 2008-07-02
erm no one?

---

