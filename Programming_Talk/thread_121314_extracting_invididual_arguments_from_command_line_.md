---
title: "extracting invididual arguments from command line argument array"
date: 2006-01-24
forum: Programming Talk
---

### Post by blacklantern on 2006-01-24
First and foremost, I'm working in C here.

I'm using command line arguments to pass in a port number that I'd like a socket to bind to in my program. My assignment requires that the TA be able to put in some arbitrary port number. Problem is, the argv is a pointer to a character array. My program will be called 'sender' and 'receiver,' and for example, the sender will be called like so:

sender 10001 11.234.124.23:10002

Where 10001 is the port number of the sender and 10002 is the port number of the receiver. The argv array will hold ascii, I'm guessing. How can I extract the first argument and change it to binary?

---

### Post by jerome bettis on 2006-01-24
```
#include <stdio.h>

int main(int argc, char* argv[])  {
    if (argc > 2)  {
        int port = 0;
        sscanf(argv[1], "%d", &port);
        printf("port = %d\n", port);
    } else  {
        printf("no arg given\n");
    }
    return 0;
}
```

---

### Post by LordHunter317 on 2006-01-24
sscanf() is the devil and should be avoided at all possible costs.  Use atoi() if possible, though it's not exceptionally better.

---

### Post by blacklantern on 2006-01-24
Thanx.

And for followup:


sender 10001 11.234.124.23:10002

How would I extract the ip address from the second argument? That is, how would I stop once the colon is reached? I'm assuming sscanf doesn't stop until it sees the null-terminated end of the string.

---

### Post by LordHunter317 on 2006-01-25
You can make sscanf() stop, with a proper format string.  A better option would be to saerch for the ':', copy the first part of the string, and then copy the second half; or use strspn() or strtok().  Unfortunately, C has no awesome string handling functions when it comes to even rudimentary parsing.  

If you get stuck, I'll post hints.

---

### Post by blacklantern on 2006-01-25
Thanx Lordhunter - I knew there had to be a function out there. If I get stuck, I'll let you know.

---

### Post by jerome bettis on 2006-01-25
[quote=LordHunter317]sscanf() is the devil and should be avoided at all possible costs.  Use atoi() if possible, though it's not exceptionally better.[/quote]

are any native C functions NOT the devil??? hah  i was going to mention atoi() but i thought sscanf() was not as bad ... i looked for snscanf() but it doesn't exist ..  this is my main beef with C as opposed to C++ .. there's acceptable easy ways to do this type of stuff in C++.  whereas C has been around forever and all the important functions are still not recommended to use.  i can't wait till C dissappears [-o<

strtok should never be used ever but if you're stuck with C what are you supposed to do?

i'm wondering what you're doing for sockets, maybe the library can take the ip address like a string?  if not it probably has some wacky defined type for an ip address you might have to look at before you can create the socket.

---

### Post by LordHunter317 on 2006-01-25
[QUOTE=jerome bettis]are any native C functions NOT the devil???[/quote]A very select few, yes.

[quote[ hah  i was going to mention atoi() but i thought sscanf() was not as bad ...[/quote]sscanf is worse, and even a length-checking version would be worse.  The whole scanf() family is to be ignored.

> i'm wondering what you're doing for sockets, maybe the library can take the ip address like a string?Not in that form, though.

---

### Post by LordHunter317 on 2006-01-25
I should point out I mentioned strtok() and strspn() but they're to be avoided too, I wasn't clear on that (strtok() should never be used in new programs, strspn() shouldn't be used except as a replacement for strtok()).  The "correct" way to do is it search for the ':', do the pointer artihmetic, make the copies, and deal with those.  

At anyrate, use of strtok() or strspn() is going to require pointer math and copying *anyway* and the resulting code will be less clear.

---

### Post by blacklantern on 2006-01-25
Yeah, I jus now realized that something is wrong with strtok(). For some reason, the when I do a gethostbyname() with the hostname string extracted from the argument with strtok(), I get an herror of 'Unknown Host.' However, when I created a new string initialized for testing purposes with the name of the host I'm trying to connect to, the gethostbyname() completes. Strange thing is, when I do a strcmp() between the tested string and the one gotten with strtok, the function returns a zero - no difference between the strings.

---

