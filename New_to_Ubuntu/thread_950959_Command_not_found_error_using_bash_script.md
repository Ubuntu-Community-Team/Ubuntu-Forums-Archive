---
title: "Command not found error using bash script"
date: 2008-10-17
forum: New to Ubuntu
---

### Post by doriggidy on 2008-10-17
Hello All, 
Just installed Ubuntu last night. Have a basic question as I play around with this.

I need to run a few simple scripts and am getting "command not found  errors". I'm also not referencing variable properly.

Here are the examples:

test01.sh 
---------
#!/bin/bash
echo "Hello,World"

When I run this from the command line ./test01.sh it returns, as expected Hello,World

test02.sh
---------
#!/bin/bash
$a="Hello,World"
echo $a

When I run this from the command line ./test02.sh it returns, unexpectedly ./test02.sh line3: =Hello,World: command not found

What am I missing?

Thanks

---

### Post by Sarmacid on 2008-10-17
Try 
a="Hello,World"
echo "$a"

---

### Post by bodhi.zazen on 2008-10-17
It is syntax

the correct syntax is ```
a="Hello,World"
```not > **[COLOR=red]$[/COLOR]**a="Hello,World"

Edit: Or what [Sarmacid]("http://ubuntuforums.org/member.php?u=597914") said :twisted:

---

### Post by doriggidy on 2008-10-17
thanks guys...duh for me!

---

### Post by saj0577 on 2008-10-17
Remember to mark as solved please. 

Thanks
Saj

---

