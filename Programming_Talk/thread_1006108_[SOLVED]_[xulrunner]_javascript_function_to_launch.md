---
title: "[SOLVED] [xulrunner] javascript function to launch bash script?"
date: 2008-12-09
forum: Programming Talk
---

### Post by lovinglinux on 2008-12-09
I'm creating a simple interface for my shell scripts using xulrunner and I need to create a javascript function to launch them.

The problem is that I'm a completely javascript noob, but it seems the only way I will be able do this.

I'm searching the web for two days and the only thing I could find was this:

```
var shell = "/bin/sh";

	var file = Components.classes["@mozilla.org/file/local;1"]
             .createInstance(Components.interfaces.nsILocalFile);

	file.initWithPath(shell);
           
           
	var process = Components.classes["@mozilla.org/process/util;1"]
                    .createInstance(Components.interfaces.nsIProcess);

	process.init(file);
           

	var args = ["/path/to/script","arg1","arg2","etc"];       

	process.run(false, args, args.length);
```

I don't have any idea if this code work, because nobody commented if it does and I really don't know how to use it. I tried to put the code above between a function and calling it with **oncommand="myfunction();"**, but it doesn't work and I don't know if I'm doing something wrong (probably).

So, any help would be much appreciated.

---

### Post by lovinglinux on 2008-12-10
Nevermind. I figure it out, after lots of reading and testing.

If someone else is interested, here is the step-by-step for dummies like me:

Create a "functions.js" file inside the extension content folder and add the following code:

```

function executeBash() {
   
var file = Components.classes["@mozilla.org/file/local;1"]
                     .createInstance(Components.interfaces.nsILocalFile);
file.initWithPath("[COLOR="Red"]/path/to/script[/COLOR]");

var process = Components.classes["@mozilla.org/process/util;1"]
                        .createInstance(Components.interfaces.nsIProcess);
process.init(file);

var args = ["[COLOR="Red"]argument1[/COLOR]", "[COLOR="Red"]argument2[/COLOR]"];
process.run(false, args, args.length);

}
```

Text in red should be replaced to suit your needs.

Then include the script in the xul page you will call the function from:

```
<script type="application/x-javascript" src="chrome://[COLOR="Red"]yourextension[/COLOR]/content/functions.js"/>
```

and call the extension adding 

```
onclick="executeBash();" 
```

to the button that will perform the action.

---

### Post by bander013 on 2009-12-14
You are my hero! :D

---

### Post by lovinglinux on 2009-12-14
> **bander013 said:**
> You are my hero! :D

Hey, I feel the need to post some updates, because this thread is old. I have been working a lot on my Firefox extensions since then and in fact I have almost completely moved away from bash. Mozilla validation tool flags bash scripts launched by the browser as insecure. Well, I can imagine why.

I still have a couple of bash commands where I couldn't port the code to javascript, but I use them only when necessary and most of the time I make a code to launch a warning that the browser is about to run a shell script and automatically copy it to the clipboard, so the user can verify it's integrity.

Perhaps I'm paranoid, but I don't have much knowledge about browser security in the coding level, so better be safe than sorry.

---

### Post by jwh777 on 2011-08-22
lovinglinux, 

I'm new to XULRunner myself, and have a question for you pertaining to it's js implementation; is it possible to run a js script directly from the C++ backend in a sheel like environment? I would like to use the 
Components.classes["@mozilla.org/network/io-service;1"]           .getService(Components.interfaces.nsIIOService); without instantiating 

thanks in advance

---

### Post by lovinglinux on 2011-08-23
> **jwh777 said:**
> lovinglinux, 

I'm new to XULRunner myself, and have a question for you pertaining to it's js implementation; is it possible to run a js script directly from the C++ backend in a sheel like environment? I would like to use the 
Components.classes["@mozilla.org/network/io-service;1"]           .getService(Components.interfaces.nsIIOService); without instantiating 

thanks in advance

Unfortunately, I have no experience with C++ so I can't answer your question.

---

### Post by spiralciric on 2012-12-04
Can you tell me if current Xulrunner can execute bash scripts or commands like this:
sudo apt-get install ...
sh ./script.sh
and similar?

I would not like to get into it if I cannot do what I need.

---

### Post by nothingspecial on 2012-12-04
Please start a new thread rather than bumping an old one to the top.

Closed.

---

