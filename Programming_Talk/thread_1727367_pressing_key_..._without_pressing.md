---
title: "pressing key ... without pressing"
date: 2011-04-12
forum: Programming Talk
---

### Post by doombyte on 2011-04-12
Hi,
I try to call ssh terminal from java program. With help of Ganymed SSH-2  for Java I can easy send and execute bash commandos  and getting back  the result:
```

Session sess = conn.openSession();
sess.execCommand("uname -a && date && uptime && who");
```Is there any bash command which will "improvise" pressing Tab key in the bash ?

thank you for any help
doombyte

---

### Post by hakermania on 2011-04-12
If you mean that [Tab] completes the word, if this is the only one that exists, I think you could use instead *, i.e. ls eisai_malakas*.txt instead of eisai_malakas [Tab] to complete the full filename eisai_malakas_kai_ton_pairneis.txt

---

### Post by cgroza on 2011-04-12
Try putting the tab character ( "\t" ) there where you would press the Tab key.

---

### Post by doombyte on 2011-04-12
hi,
thanks for your replay,
hakermania,
 yes what I need this is this TAB function completes word, or listening  I need it as a result back to my Java program.

cgroza,
"/T" did't work , or I am not using it correctly :(
I do it this way  :
```

sess.execCommand("/t && /t");

```
The result look the same if you would put it directly in terminal.
Bash don't know what to do with that.
any Idea?

---

### Post by doombyte on 2011-04-12
The other way witch I am trying is with xdotool tool : 
This script is doing exactly what I need, but just when I start ssh with flag -X : 
```
#
!/bin/bash
eval xdotool type 'exi'
eval xdotool key Tab Tab

```

But after using it from Java : 
```

sess.requestX11Forwarding(hostname, 6010, null, true);
sess.execCommand("xdotool type 'exi' && xdotool key Tab Tab");

```

I am getting error : 
```
Error: Can't open display: localhost:11.0
Failed creating new xdo instance
ExitCode: 1
```
:confused:

---

### Post by cgroza on 2011-04-12
> **doombyte said:**
> hi,
thanks for your replay,
hakermania,
 yes what I need this is this TAB function completes word, or listening  I need it as a result back to my Java program.

cgroza,
"/T" did't work , or I am not using it correctly :(
I do it this way  :
```

sess.execCommand("/t && /t");

```The result look the same if you would put it directly in terminal.
Bash don't know what to do with that.
any Idea?
Well, you cannot complete "nothing", maybe I did not understand your question correctly.

---

### Post by slavik on 2011-04-13
you forgot the part where the terminal has to support the tab. as it stands there is no terminal. in fact, try running sudo or ssh within that connection, won't work ...

finding out what the error returned will be is left as an exercise to the reader.

---

### Post by doombyte on 2011-04-13
Hi slavik,
I don't understand, witch part do you mean?
I am login in to the ssh terminal : 
```

Connection conn = new Connection(hostname);
conn.connect();
boolean isAuthenticated = conn.authenticateWithPassword(username, password);
  if (isAuthenticated == false)
                throw new IOException("Authentication failed.");   
Session sess = conn.openSession();
sess.execCommand("date");       

```And I am getting back result to the jave from bash: 
 ```

Mi 13. Apr 12:13:49 CEST 2011
ExitCode: null
```

[EDIT]
In between I found this 2 ways witch are working direct on ssh terminal : 
xdotool type 'exi' && xdotool key Tab Tab
and
xvkbd 2>/dev/null -text "\t\t"
but no result :(

---

### Post by slavik on 2011-04-13
> **doombyte said:**
> Hi slavik,
I don't understand, witch part do you mean?
I am login in to the ssh terminal : 
```

Connection conn = new Connection(hostname);
conn.connect();
boolean isAuthenticated = conn.authenticateWithPassword(username, password);
  if (isAuthenticated == false)
                throw new IOException("Authentication failed.");   
Session sess = conn.openSession();
sess.execCommand("date");       

```And I am getting back result to the jave from bash: 
 ```

Mi 13. Apr 12:13:49 CEST 2011
ExitCode: null
```

[EDIT]
In between I found this 2 ways witch are working direct on ssh terminal : 
xdotool type 'exi' && xdotool key Tab Tab
and
xvkbd 2>/dev/null -text "\t\t"
but no result :(
you haven't read my post properly ... please re-read it, carefully.

---

### Post by doombyte on 2011-04-13
> **slavik said:**
> you haven't read my post properly ... please re-read it, carefully.
Hi , probably I understand wrong your post ? 
Did you mean to log in to terminal and than run java program ?
There are no errors printing out there.
But if I am using
 ```
sess.requestX11Forwarding(hostname, 6010, null, false);
``` 
than I am getting error on ssh terminal : 
```
X11 connection rejected because of wrong authentication.
```
Or if I am wrong , could you please explain what do you mean with :
> part where the terminal has to support the tab.  
thank you && greetings
doombyte

---

### Post by slavik on 2011-04-14
I will re-write what I wrote above:
Once you open the ssh connection with your favorite ssh library, try running sudo or ssh to another system within that connection.

There isn't any way for me to be clearer here. You are not understanding that the shell is not the only thing reading the input. There is a terminal involved. Terminals have drivers. Terminal drivers can disable echo. If a terminal does not exist, you cannot disable echo.

---

