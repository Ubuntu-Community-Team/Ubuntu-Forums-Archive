---
title: "install .deb file"
date: 2018-07-23
forum: New to Ubuntu
---

### Post by abdossamad2003 on 2018-07-23
hi everyone
I am new player to ubuntu
how can i install .deb file in ubuntu with dependency? (in terminal or without it)
my ubunut is 18.04

Many Thanks
samad

---

### Post by slickymaster on 2018-07-23
See this: [How do I install a .deb file via the command line?]("https://askubuntu.com/questions/40779/how-do-i-install-a-deb-file-via-the-command-line")

---

### Post by twily2018 on 2018-07-23
open the terminal and type: 

```
sudo dpkg -i yourdebfile.deb
```

If you get an error after running this command then type:

```
sudo apt -f install
```

That should do it.

To know more about specific commands you can also run the **man **command. Like:


```
man dpkg
```

It will usually show you information about a specific commands and all the things you can do with it.

---

### Post by monkeybrain20122 on 2018-07-23
Just click it. Then the software centre would install it.

---

### Post by monkeybrain20122 on 2018-07-23
> **twily2018 said:**
> open the terminal and type: 

```
sudo dpkg -i yourdebfile.deb
```

If you get an error after running this command then type:

```
sudo apt -f install
```

That should do it.

To know more about specific commands you can also run the **man **command. Like:


```
man dpkg
```

It will usually show you information about a specific commands and all the things you can do with it.



If you must use command

```
sudo apt install /absolute/path/to/deb 
```

would do it.

I don't recommend -f if errors are encountered without knowing what the errors are. It might install the .deb while your underlying problems remain unresolved.

But this is a new user section, why make it more complicated than has to? Man dpkg to install a .deb?? BTW dpkg doesn't install dependencies.

---

### Post by Autodave on 2018-07-23
Or, you could install the package *gdebi *and make it rather easy. Gdebi is in the Software Center and *synaptic.*

---

### Post by twily2018 on 2018-07-23
> **monkeybrain20122 said:**
> If you must use command

```
sudo apt install /absolute/path/to/deb 
```

would do it.

I don't recommend -f if errors are encountered without knowing what the errors are. It might install the .deb while your underlying problems remain unresolved.

But this is a new user section, why make it more complicated than has to? Man dpkg to install a .deb?? BTW dpkg doesn't install dependencies.

-f will get the dependencies.

---

### Post by monkeybrain20122 on 2018-07-23
> **twily2018 said:**
> -f will get the dependencies.
 No, apt install would get the dependencies already.

---

### Post by twily2018 on 2018-07-24
> **monkeybrain20122 said:**
> No, apt install would get the dependencies already.

I see now. I didn't know that. It just never auto-completed the packages in the same directory, had to write the full path while dpkg did it in the same directory and then I just had to run apt -f install which then gets the deps and install it. I guess it's just a matter of preference. For 5 years on debian I always used dpkg. lol

---

### Post by monkeybrain20122 on 2018-07-24
> **twily2018 said:**
> I see now. I didn't know that. It just never auto-completed the packages in the same directory, had to write the full path while dpkg did it in the same directory and then I just had to run apt -f install which then gets the deps and install it. I guess it's just a matter of preference. For 5 years on debian I always used dpkg. lol

Using apt to install deb is new so before you could only use dpkg. 

I should have said /path/to/deb rather than absolute path, so if you are in the directory of the deb just do

sudo apt install ./name of deb

---

