---
title: "Want to remove _ from files and tar and send them to a server"
date: 2011-06-15
forum: Programming Talk
---

### Post by Apoorvbarwa on 2011-06-15
Hi
I want to rename some files in a directory say /dir/dir1 . The files in this directory are in the format file_001.aa. I want to rename them and change them to file001.aa(basically remove the _ from the filename). After this i have to tar them and then send it to a server.Could anyone help me out here.

I have tried the following for renaming them

i go to the directory and then execute the following:

**for i in *;do mv $i $(echo $i | sed 's/_//g');done**

then i have to exit and i do 

**tar -cf archive.tar /dir/dir1**

can anyone give me solution and also can this be done using only the find command with pipes.

Thanks in advance

---

### Post by Apoorvbarwa on 2011-06-15
Also could you please explain it as i am a bit new to shell scripting

---

### Post by BkkBonanza on 2011-06-15
You can do the string manipulation right in shell without sed.
You might make a shell script that takes the path to the dir to work in and the target archive.
eg. (untested!)

```

#!/bin/bash

if [[ $# -lt 2 ]]; then
  echo "Usage: $0 <dir> <tarpath>"
  exit
fi

for f in $1/*; do mv $f ${f//_/}; done
tar -cf $2 $1

```

The ${f//_/} is the bash syntax for string search/replace. 
See [this page]("http://tldp.org/LDP/abs/html/string-manipulation.html") for more examples of string manipulation.

In my script here I first check if the correct number of cmd args are provided and if not then print a help message. Then I just use for to loop over each file in the given directory and do the mv command (same as rename), and then tar to create the archive.

---

### Post by geirha on 2011-06-15
See [http://mywiki.wooledge.org/BashFAQ/030](http://mywiki.wooledge.org/BashFAQ/030).

Now for your question regarding find, you need to be more specific. What does your directory tree look like? do you want both files and directories renamed? Do you want the entire tree archived, or one archive per directory?

@BkkBonanza There are several problems with that script. The most important one is the complete lack of quotes, which in this case will even give a syntax error. Please see [http://mywiki.wooledge.org/Arguments](http://mywiki.wooledge.org/Arguments)

Also, the ABS page you linked to regarding string manipulation is really not a good page at all. It uses inconsistent syntax, randomly omits quoting, parses ls output and even confuse you further by showing useless examples of expr. This is a much better resource: [http://mywiki.wooledge.org/BashFAQ/100](http://mywiki.wooledge.org/BashFAQ/100)

The Advanced Bash-scripting Guide is best avoided all together.

---

### Post by BkkBonanza on 2011-06-15
I just wrote that quickly as an example and noted that it was **untested**. I've gone back and added quotes and fixed the endif to fi booboo, things that I would have found on a first run. 

I've used that strings manipulation for years as a reference when I can't recall syntax. Maybe it's not the best but it has proven itself helpful. 

I quite resent your attitude to bashing someone who is just trying to help out here. At least I tried to help. Slamming user's help like you do will only lead to a forum with few people willing to share and help.

---

### Post by geirha on 2011-06-16
> **BkkBonanza said:**
> 
I quite resent your attitude to bashing someone who is just trying to help out here. At least I tried to help. Slamming user's help like you do will only lead to a forum with few people willing to share and help.

Well I'm sorry if you felt I was "bashing" you. My intention was to criticize the shell code, which is missing quotes. Failing to take word-splitting into account may lead to unexpected bugs and in worst cases cause corruption or data loss. The page I linked to in my previous post explains why.

You fixed the syntax errors, that's fine, but those aren't the dangerous bugs, it's the unquoted parameter expansions. Now, the short snippet you posted isn't dangerous in itself, it will give unexpected errors if filnames containing certain bash syntax happens to be in the directory, but if someone were to extend that code, and keeping in the line of not quoting expansions, bad things may indeed happen. So, I generally point out these bugs when I see them. 

A fixed version of the for-loop and tar command would look something like this:
```

for f in "$1"/*_*; do mv "$f" "${f//_}"; done
tar -cf "$2" "$1"

```

---

### Post by Apoorvbarwa on 2011-06-20
Hi ... I managed to create a tar file of the renamed files ... using the above script .... can anyone tell me how to ftp it ...
can i just say 

ftp 100.101.10.1
cd "dir/to/send/to/"
put xyz.tar
bye

Can anyone suggest

---

