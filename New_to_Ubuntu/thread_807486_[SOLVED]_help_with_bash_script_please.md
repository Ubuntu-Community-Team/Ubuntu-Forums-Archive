---
title: "[SOLVED] help with bash script please"
date: 2008-05-25
forum: New to Ubuntu
---

### Post by slughappy1 on 2008-05-25
I want to write a script so that I can simply execute the script and it will install all of the programs I want. I tend to try different distros and then come back to Ubuntu. I want to make my life easier to get my Ubuntu install back up and running. So I have a couple of questions.

Where would be a good place to learn how to write bash scripts? Scripts that I can tell it to apt-get install some_package. Then when it find the package it generally  asks if I want to install. I then want the script to say yes or Y. So I guess I just want to be able to install the program without touching anything after executing the script.

---

### Post by cardinals_fan on 2008-05-25
[http://www.ibm.com/developerworks/library/l-bash.html](http://www.ibm.com/developerworks/library/l-bash.html)

---

### Post by slughappy1 on 2008-05-26
I just thought about something. Does anyone know if making a .deb would work? Or if it might actually be easier and work better?

---

### Post by decoherence on 2008-05-26
Making a bash script is simplicity itself!

Making a .deb metapackage is probably overkill for what you want and way more difficult (though a very useful thing to learn!)

Here's your bash script

```
#!/bin/bash

apt-get update
apt-get -f install
apt-get install program1 program2 program3 program4 etc
```

If you have any experience at the command line, you'll notice that this is just a list of commands. Indeed, that's all a bash script is; a list of commands (sometimes with extra formatting to illustrate loops and conditionals.)

Since the script runs apt-get, it needs to be run as root or with sudo. Also things like making the script executable and putting it in the path will make it simpler to call. To run the script without these extra steps, you'd say "sudo bash /path/to/script"

hope that helps

---

### Post by slughappy1 on 2008-05-26
What about if you need to add a repository? For example to install btnx? I am making an Ubuntu page on my website, [here]("http://slughappy.com/?page_id=10"). I mess with my installation sometimes and I want to make a simple way to get my normal installation back.

---

### Post by slughappy1 on 2008-05-26
How would you ask a question of the user in a bash script? For example:```
printf "After the script is executed it will restart you computer."
x = printf "Do you still want to run the script (Y,n)? "
if( x == 'Y')
run script
else break
```

---

### Post by slughappy1 on 2008-05-26
Ok so this is what I have so far ```
#!/bin/bash

echo "After the script is executed it will restart you computer."
echo -n "Do you still want to run the script (Y,n)? "
read S1
S2= "Y"
if [ $S1 = $S2 ]; then
	echo "It worked"
else
	echo "Denied"
fi
```
But I get this error
```
jason@Tux:~$ sudo bash /home/jason/Scripts/test
After the script is executed it will restart you computer.
Do you still want to run the script (Y,n)? Y
/home/jason/Scripts/test: line 6: Y: command not found
/home/jason/Scripts/test: line 7: [: Y: unary operator expected
Denied
jason@Tux:~$ 

```

---

### Post by slughappy1 on 2008-05-26
Never mind, I figured it out```
#!/bin/bash

echo "After the script is executed it will restart you computer."
echo -n "Do you still want to run the script (Y,n)? "
read S1
if [ $S1 = Y ]
then
	echo "It worked"
else
	echo "Denied"
fi
```

---

### Post by decoherence on 2008-05-27
Glad I could help! lol... Seriously tho, nice job figuring it all out! :D

When debugging bash scripts it can be handy to run them like so

```
bash -x /path/to/script
```

More useful in complicated scripts, but it's nice to be able to watch it step through each command.

---

