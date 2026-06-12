---
title: "Is there a bash command..."
date: 2008-03-22
forum: Programming Talk
---

### Post by POW R TOC H on 2008-03-22
..or a program that outputs the PID of the process that currently has keyboard focus?

---

### Post by stroyan on 2008-03-23
The xdpyinfo command will tell you the window id of the window that currently has focus.  But the X server can't map a window id to a process id.  X11 is a network based client/server mechanism.  It is entirely possible that the client that created a window is on a different system.  You can get a list of details about X11 clients using "xlsclient -l".
```

function focus_window {
  read d1 d2 w d3 <<< $(xdpyinfo | grep focus)
  echo ${w/,}
}
function client_info {
  id=${1: -9:4}
  xlsclients -l |
    while read window
      read machine
      read name
      read icon
      read cmd
      read class
      do
        if [[ $window =~ $id ]] ;then
          echo $window
	  echo $machine
	  echo $name
	  echo $icon
	  echo $cmd
	  echo $class
        fi
      done
}
while sleep 1; do client_info $(focus_window);done

```

---

### Post by POW R TOC H on 2008-03-23
Thanks! Where do you learn all that?? (This is a rhetorical question, it means : please point me to some good books and web sites where I can learn more about bash)

---

### Post by stroyan on 2008-03-23
There is a lot of good material in the 'Advanced bash scripting guide'.
See [http://tldp.org/LDP/abs/html/](http://tldp.org/LDP/abs/html/) .
Or install the abs-guide package from the ubuntu multiverse repository.
That package includes lots of examples in /usr/share/doc/abs-guide/examples/ .

Much of the power of shell scripts comes from the ability to draw on a wide variety of commands such as xdpyinfo and xlsclients.  Finding interesting commands can be a challenge.  You can use 'man -k' with interesting keywords to fish for useful commands.  But that only covers installed commands.  You may need to use 'apt-cache search' or synaptic's search function to find out about commands in packages that are not already installed.

Another option is to just spend some time looking through /usr/bin and seeing what is there and what man has to say about them.  It isn't work if you find it interesting. ;-)

---

### Post by Zwack on 2008-03-24
I would also suggest most books about Unix in general should cover X windows and what is a server and what is a client... 

I remember my MSc supervisor coding up a quick script while we were talking (and he was supervising an undergraduate class) to run round every machine in the room playing random sounds...

(So I showed him how to fake sending e-mail from anyone to anyone else with the telnet command...)  

But once you understand what you're working with you will understand why it could be impossible to answer some questions.  

Do random searches on google as well for any interesting sounding keyword combinations.  "window server client unix" for example gives an interexting collection of links You should then be able to follow chains of links from site to site...  Understand the architecture and then the practicalities become easier.

I hope that this helps,

Z.

---

