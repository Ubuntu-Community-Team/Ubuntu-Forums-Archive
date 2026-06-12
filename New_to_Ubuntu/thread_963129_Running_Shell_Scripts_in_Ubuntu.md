---
title: "Running Shell Scripts in Ubuntu"
date: 2008-10-29
forum: New to Ubuntu
---

### Post by Jodyman on 2008-10-29
If I use the shebang line in my scripts, how come linux/ubuntu can't execute them?

I have to use:

$ sh test.sh              with #!/bin/sh

or

$ ksh test.sh             with #!/usr/bin/ksh

?????

Wierd!:(

---

### Post by igknighted on 2008-10-29
can you post one of your scripts?  Maybe we could find the problem.

---

### Post by Jodyman on 2008-10-29
#!/usr/bin/ksh

function get_time
  {
     HH=$(( $(date +%H ) + 1 ))  
     MM=$(( $(date +%M ) + 1 ))
  } 

#print "${1##*/}"

get_time
CNT=30
print ${CNT}
print ${MM}

    until [[ $CNT -eq 0 || $MM -ge 37 ]]
      do
      sleep 2
      print "CNT: ${CNT} MM+1: ${MM}"

      CNT=$(( $CNT - 1 ))
      get_time
      
      done

---

### Post by Jodyman on 2008-10-29
You'll need to load ksh through the Synaptic Package Manager to use ksh.

I've chmod 755 the script but still need to preface the line with the shell to get them to work.

---

### Post by igknighted on 2008-10-29
Hmm... works perfectly as is for me just running it with ./script.sh

---

### Post by DGortze380 on 2008-10-29
> **Jodyman said:**
> If I use the shebang line in my scripts, how come linux/ubuntu can't execute them?

I have to use:

$ sh test.sh              with #!/bin/sh

or

$ ksh test.sh             with #!/usr/bin/ksh

?????

Wierd!:(

IIRC you need to install ksh, bash is default in ubuntu. 

sudo apt-get install ksh

---

### Post by igknighted on 2008-10-30
> **DGortze380 said:**
> IIRC you need to install ksh, bash is default in ubuntu. 

sudo apt-get install ksh

He knows... note in post (4 I think?) how he told me that I needed to install ksh from synaptic before testing.

@OP: using sh to launch the script is the wrong interpreter.  What if you use 'ksh script.sh' instead?  Or just use the './script.sh'?

---

### Post by Jodyman on 2008-10-30
In HPUX, you only need to chmod +x the shell script, put the shebang line in the start of the script and type:  test.sh at the prompt.

It seems to execute a script in Linux, you must use the ./test.sh or in my case you can also use:  ksh test.sh to run an executable script.

Maybe there are some system settings to allow you to just type:  test.sh 
and it would run the shell script.

Jody

---

### Post by ad_267 on 2008-10-30
See [http://www.linuxforums.org/forum/misc/27942-linux-doesnt-automatically-add-current-directory-path.html](http://www.linuxforums.org/forum/misc/27942-linux-doesnt-automatically-add-current-directory-path.html)

You can just add . to your path in your .bashrc file.

---

### Post by Jodyman on 2008-11-01
I've greped my .bashrc file for path, there isn't one.

What parameters or directories should be listed in my path?

I find no 'man path' results on my machine.

Jody

PS - Is there such a thing as a .kshrc also?  I'm trying to set up ksh on my machine also.  How can I set it to be my default shell instead of bash?

---

### Post by ad_267 on 2008-11-01
I'm not sure about ksh, but for bash you can put this in your .bashrc:

PATH=$PATH:.

It would probably be the same for ksh.

Your path is just a list of paths separated with a colon, so that sets your path to be whatever it was before, with . added at the end.

You can set your default shell under System - Administration - Users and Groups. Then in the user properties it is under the Advanced tab.

---

### Post by Jodyman on 2008-11-02
Putting the path in .bashrc also fixed it when i run the korn shell too.  Thanks for your help.  It now works as expected.

Jody

---

