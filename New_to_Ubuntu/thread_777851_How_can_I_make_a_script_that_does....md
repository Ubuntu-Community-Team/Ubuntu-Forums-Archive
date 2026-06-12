---
title: "How can I make a script that does..."
date: 2008-05-01
forum: New to Ubuntu
---

### Post by dwally89 on 2008-05-01
Hi,

I've never written a script before, but how could I write one, that when executed will execute the following commands in order, in the terminal:

```

sudo apt-get autoclean
sudo apt-get clean
sudo apt-get autoremove
```

Thanks

---

### Post by Nxion on 2008-05-01
> **dwally89 said:**
> Hi,

I've never written a script before, but how could I write one, that when executed will execute the following commands in order, in the terminal:

```

sudo apt-get autoclean
sudo apt-get clean
sudo apt-get autoremove
```Thanks

Put the commands in file and call it like apt.sh

```
sudo gedit cleanup.sh
```Than paste this:

```
 sudo apt-get autoclean && sudo apt-get clean && sudo apt-get autoremove
```Save it and make it executable:

```
sudo chmod +x cleanup.sh
```Then run it:

```
sudo ./cleanup.sh
```

---

### Post by dwally89 on 2008-05-01
Thanks :-)
Sorry to be picky, but could I make it say what it is running before it runs it, e.g.:

```

autoclean
then runs it
clean
then runs it
autoremove
then runs it
```

Thanks

---

### Post by squaregoldfish on 2008-05-01
Simply add a line saying 'echo "<message>"' wherever you want the script to say something.

So your script would be:

```
echo "Running autoclean..."
sudo apt-get autoclean
echo "Running clean..."
sudo apt-get clean
echo "Running autoremove..."
sudo apt-get autoremove
echo "Finished!"
```

Steve.

---

### Post by Nxion on 2008-05-01
Sorry about that. My bad :(

Put this in a file instead

```
echo "Running autoclean"
sudo apt-get autoclean
echo "Running clean"
sudo apt-get clean
echo "Running autoremove"
sudo apt-get autoremove
echo "Done"
```

Follow the above steps to make the file executable and you should be fine.

---

### Post by Nxion on 2008-05-01
> **squaregoldfish said:**
> Simply add a line saying 'echo "<message>"' wherever you want the script to say something.

So your script would be:

```
echo "Running autoclean..."
sudo apt-get autoclean
echo "Running clean..."
sudo apt-get clean
echo "Running autoremove..."
sudo apt-get autoremove
echo "Finished!"
```Steve.

Awwww you beat me to it :(

:(

---

### Post by dwally89 on 2008-05-01
Thanks :-)

---

### Post by brian_p on 2008-05-01
> **dwally89 said:**
> Thanks :-)
Sorry to be picky, but could I make it say what it is running before it runs it, e.g.:

```

autoclean
then runs it
clean
then runs it
autoremove
then runs it
```

Thanks

First off: the first line of the file needs to be

```
#!/bin/bash
```

otherwise it will not execute.

To answer your question: precede each command with

```
echo "This is the command running"
```

To ask a question of my own: why run 'clean' **and** 'autoclean'? 'clean' does what 'autoclean' does plus some more.

---

### Post by dwally89 on 2008-05-01
I just remember reading about those commands on [http://www.stchman.com/cleanup.html](http://www.stchman.com/cleanup.html).

And also it seems to be executing even without using #!/bin/bash

---

### Post by nhandler on 2008-05-01
> **dwally89 said:**
> I just remember reading about those commands on [http://www.stchman.com/cleanup.html](http://www.stchman.com/cleanup.html).

And also it seems to be executing even without using #!/bin/bash

It will execute fine without #!/bin/bash, but it is a good idea to include that line at the top of your script. It tells the computer that the script should be executed by bash. It will allow the script to be run on a much wider range of computers (where bash might not be the default shell).

---

### Post by dwally89 on 2008-05-01
OK Thanks

---

### Post by mali2297 on 2008-05-01
If you start the script with sudo, then you can skip sudo in the script.

---

