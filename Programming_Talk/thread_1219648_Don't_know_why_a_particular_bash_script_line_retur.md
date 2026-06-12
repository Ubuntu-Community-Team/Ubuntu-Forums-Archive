---
title: "Don't know why a particular bash script line returns NULL"
date: 2009-07-22
forum: Programming Talk
---

### Post by Neovos on 2009-07-22
I'm sure this is a bit juvenile for all the serious programming questions that go on in this particular category, (which I hope to contribute to eventually, I'll be learning C++ and prolog very soon) but for now, I have a bash question.

I'm working on some screen shifting scripts using nv-control-dpy and if you look at the code below, every section in between the pipes works fine and as desired, but when it gets to zenity, the input from the pipe is NULL for some reason and I don't get the list that very clearly gets produced from "paste -s." My hunch is that it isn't leaving paste in standard out for some reason but if so, what program can do that for me?

```
nv-control-dpy --probe-dpys | grep "    [A-Z]" | awk '{print$1}' | paste -s | zenity --list --radiolist --text "Select a port to send the GUI" --column "" --column "Detected Ports"
```

---

### Post by stroyan on 2009-07-22
Your trouble is not with paste but with zenity.
The "--list --radiolist" does not take column data from stdin.
It needs the column data as arguments.
You could use a bash array to hold the arguments.
That has the nice effect of allowing you to use the "${A[@]}" notation.
That form allows array elements to contain spaces and not get broken into multiple arguments.

```

unset PORTS
while read P Remainder
do
  PORTS+=("$P")
done <<<"$(nv-control-dpy --probe-dpys | grep "    [A-Z]")"
unset ZDATA
FOR P in "${PORTS[@]}"
do
  ZDATA+=(FALSE "$P")
done
zenity --list --radiolist --text "Select a port to send the GUI" --column "" --column "Detected Ports" "${ZDATA[@]}"

```

---

### Post by Neovos on 2009-07-28
I see what your doing now. I had some syntax errors when trying to run it though, perhaps that was my not telling you that this is sh and not bash? Should I use one and not the other? 

My message was ```
Syntax error: word unexpected (expecting ")")
``` when refering to the line "PORTS+=("$P")"

---

### Post by stroyan on 2009-07-28
bash is much more capable than dash.
dash does not implement array variables at all.

---

### Post by Neovos on 2009-07-28
I changed the top of the sript to bash from sh but am still gettin the same syntax error...

---

### Post by stroyan on 2009-07-29
It sure sounds like it is still running dash.
I can replicate that error message by using dash.
Perhaps there is a typo with your first line of "#!/bin/bash".
Or perhaps you ran the script as "sh scriptname", overriding the #!.
Try running the script as "bash scriptname".

---

### Post by Neovos on 2009-07-30
Thanks so much for you help stroyan, I was confusing sh, bash, dash. Got that cleared up but still having problems it appears:
```
brian@Apollo:~/Desktop$ bash sendgui
sendgui: line 30: syntax error near unexpected token `do'
sendgui: line 30: `			do'

```

here's the script in it's entirety thus far:
```
#!/bin/bash

# detect whether we are executing in GUI environment or terminal, detect the connected displays, and ask which port the user wants to send the GUI to.

if [ -t 1 ]  
	then
		displaylist=`nv-control-dpy --probe-dpys | grep "    [A-Z]" | awk '{print$1}'`
		echo -n "Ports Detected:\n$displaylist\n\nSend GUI to:" 
		read DISPLAY_TARGET
			if [ -z "$displaytarget" ];then
				exit 1
			fi

	else 
		unset PORTS
		while read P Remainder
			do
			PORTS+=("$P")
		done <<<"$(nv-control-dpy --probe-dpys | grep "    [A-Z]")"
		unset ZDATA
		FOR P in "${PORTS[@]}"
			do
			ZDATA+=(FALSE "$P")
	done
		displaytarget=`zenity --list --radiolist --text "Select a port to send the GUI" --column "" --column "Detected Ports" "${ZDATA[@]}"`
			if [ -z "$DISPLAY_TARGET" ];then
			exit 1
			fi
fi

exit 0 
```

What do you think?

---

### Post by stroyan on 2009-07-30
I somehow got the 'FOR P in "${PORTS[@]}"' loop changed to uppercase.
It should be 'for P in "${PORTS[@]}"'.

---

