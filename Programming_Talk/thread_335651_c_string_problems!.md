---
title: "c string problems!"
date: 2007-01-10
forum: Programming Talk
---

### Post by joey_joe_joe on 2007-01-10
i am working on a client/server app. the client sends a pasword to the server, which the server then uses for authentication. however, the password is being rejected. when i do a printf i can see the password and it is correct. when i manually try to authenticate by typing this password login is successful. 
does anyone know what might cause this. possibly extra characters being added to the string, such as newline char? is there a c fxn to strip a string down to what you would see of the string when you do a printf. i know the password is correct, i can logon with it, but when the server program attempts to logon with it, it fails.

thanks in advance.

---

### Post by Tomosaur on 2007-01-10
Are you sure your input/output streams are correct? What is the result of a printf on the server side?

---

### Post by joey_joe_joe on 2007-01-10
a printf on the server side shows the correct password. if i put a char on either side of the print it show there's no whitespaces.

printf("!%s!", str);

gives: !mypassword!

null terminated? could this affect it?

---

### Post by Tomosaur on 2007-01-10
Very odd. This is a longshot, but what's the output of cout rather than a printf? There could be a character somewhere which printf is arsing about with. Bit of a shot in the dark but anything's worth a go.

---

### Post by Lux Perpetua on 2007-01-10
> **Tomosaur said:**
> Bit of a shot in the dark but anything's worth a go....and shooting in the dark is all we can do with the information provided, meaning it would take a clairvoyant (or very lucky) programmer to solve joey's problem. joey_joe_joe, the more information you're able to post, the better the help you're likely to receive.  

Alternatively, since you seem to have control over the server as well, you can debug there yourself by making the authenticator more verbose, printing out the reason for rejecting the password (the mismatched character or hash code, etc.) That should narrow down your problem in no time.

---

### Post by jblebrun on 2007-01-10
> **joey_joe_joe said:**
> i am working on a client/server app. the client sends a pasword to the server, which the server then uses for authentication. however, the password is being rejected. when i do a printf i can see the password and it is correct. when i manually try to authenticate by typing this password login is successful. 
does anyone know what might cause this. possibly extra characters being added to the string, such as newline char? is there a c fxn to strip a string down to what you would see of the string when you do a printf. i know the password is correct, i can logon with it, but when the server program attempts to logon with it, it fails.

thanks in advance.

As someone else said, you give us hardly any information to work with. However, I'm gonna go on a hunch and guess that you've made a common error here: how are you comparing the strings? You are using strcmp/strncmp, not ==, right?

Assuming your C string is a char*, then something like:

```

char* t="abc";
char* s="abc";
if (t==s) print "True"; 

```

Will NOT print true, because you're comparing the address of the strings, not the contents. 

The correct way is
```

if (!strcmp(t,s)) print "true";

```
Because strcmp returns 0 if the strings are the same.

---

### Post by joey_joe_joe on 2007-01-11
seems to be working now....instead i have dumped the password to a textfile and read it back when needed, works fine.

---

### Post by Tomosaur on 2007-01-11
Bad idea though, unless you encrypt it.

---

### Post by joey_joe_joe on 2007-01-11
yeah, you're right. but i'm focusing on basic functionality now, i'm going to address security once everything is working.

---

### Post by Tomosaur on 2007-01-11
> **joey_joe_joe said:**
> yeah, you're right. but i'm focusing on basic functionality now, i'm going to address security once everything is working.

Ugh, you do realise that that will entail rewriting a LOT more than you think? You can't let design errors propogate throughout the system, because you WILL get headaches later on, trust me. It's much better to make sure things work how you want them to early on as you're writing them, to avoid little mistakes becoming big problems. This is called 'clean room' development. It's not about fixing errors so much as avoiding them completely.

---

### Post by ArtechnikA on 2007-01-11
> **joey_joe_joe said:**
> yeah, you're right. but i'm focusing on basic functionality now, i'm going to address security once everything is working.

interesting plan; look how well that's worked for Microsoft ...

---

### Post by joey_joe_joe on 2007-01-11
lol, this is not a commercial project, it's just a personal project. anyway, 
basic functionality is working now, does anyone know of any good tutorials to use PKI to encrypt the password when sending over TCP?

---

