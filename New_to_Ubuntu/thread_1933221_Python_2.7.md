---
title: "Python 2.7"
date: 2012-02-28
forum: New to Ubuntu
---

### Post by Joshua Parsons on 2012-02-28
Hello, I have recently downloaded ubuntu as my main OS and, I would like to install python but, when I run the idle and save my program as a .py it does not run in a console. any ideas. Please if you explain dont be vague especially with the terminal I dont know how to use it. thank you.

---

### Post by matbluvenger on 2012-02-28
Python is built in. You don't have to install anything.

And if I'm misreading the question, here's an alternate answer:

If you're trying to run a program you wrote in python on ubuntu, open terminal and do as such:
```
sudo chmod 755 filename
```


This will give the permission for said file to be executable. I don't know about .py filetype but .cpp works great for me.

Then execute it:
```
./filename
```

---

### Post by enjoijesus94 on 2012-02-29
Make Sure You Put Inside Your Script 

```
#!/usr/bin/python
```then make your application executable

```
sudo chmod +x path
```then launch it 

```
./pyapp.py
```

replace all with your correct path and filename.

:D

---

### Post by matbluvenger on 2012-02-29
Oh right, thanks! Forgot about mentioning #!usr/bin/python

---

### Post by enjoijesus94 on 2012-02-29
> **matbluvenger said:**
> Oh right, thanks! Forgot about mentioning #!usr/bin/python

hey it happens man
last week i was creating a application to organize packages inside linux when i wonder 
Why Isnt It Executing?

found out it was the the #!/usr/bin/python haha

we all make mistakes man

tell me if it works

---

### Post by matbluvenger on 2012-02-29
Yeah, I'm interested to see if OP got it done!

And enjoijesus, is there any kind of advantage to doing
```
sudo chmod +x <path>
```

over
```
sudo chmod 755 <filename>
```

or is it just different syntax?

---

### Post by Joshua Parsons on 2012-03-03
Yeah I got zero Idea I can get this far
 
1) clt+alt+t
2) sudo
 
What do I put after the sudo do I have to do like sudo /dev/python2.7/hello world.py
or just sudo hello world.py. Sorry im totall begginer

---

### Post by matbluvenger on 2012-03-03
The first one will work. But what you can do is shrink that to a shortcut directory. This will only work is you're in the directory in which the .py file is located. Otherwise it will make a new file of the same name in the directory you are in.

```
sudo pico ./hello world.py
```

or

```
sudo pico ~/hello world.py
```


Say, for instance, that file is in the /home/Downloads directory. You simply do this code to get there:

```
cd ./Downloads
```

or, again

```
cd ~/Downloads
```


"pico" is the text editing program I use. There are a multitude to choose from, I just am partial to pico.

---

