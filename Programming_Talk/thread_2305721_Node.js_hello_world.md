---
title: "Node.js hello world"
date: 2015-12-08
forum: Programming Talk
---

### Post by tumelo on 2015-12-08
I'm on LXLE. 

I ran "sudo apt-get install node"
And then made a helloworld.js file which contains "console.log("hello world");
then I ran "node helloworld.js" 

but nothing happened. I thought the hello world program would be that simple. Am I missing something?

---

### Post by spjackson on 2015-12-08
> **tumelo said:**
> 
I ran "sudo apt-get install node"

Really? The package for node.js is called "nodejs". There is a package called "node" but that is an entirely different thing.

---

### Post by tumelo on 2015-12-08
I figured it out. Apparently the package is called nodejs, not node. 

So you have to run "sudo apt-get install nodejs"

and then run the program with "nodejs helloworld.js" instead of "node helloworld.js"

---

### Post by tumelo on 2015-12-08
Sorry didn't read your response until after I figured it out and posted, but Thanks spjackson

---

