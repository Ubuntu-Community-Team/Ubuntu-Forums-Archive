---
title: "why do people start scripts #!/bin/bash and not #!/usr/bin/env bash"
date: 2012-02-27
forum: New to Ubuntu
---

### Post by josephmills on 2012-02-27
so yeah I am wondering about the shebang shabang how ever you spell it. why do people use #!/bin/bash and not #!/usr/bin/env bash ? 
Also what is the point of Ubuntu coming with Dash and not bash?
If I now change to bash will this kill all my scripts ? thanks for your time.

---

### Post by Lars Noodén on 2012-02-27
dash is smaller and faster.  It is a subset of bash, so your dash scripts should also run under bash, but it is not guaranteed that your bash scripts will also run under dash. 

[https://wiki.ubuntu.com/DashAsBinSh](https://wiki.ubuntu.com/DashAsBinSh)

---

### Post by nothingspecial on 2012-02-27
Fixed typo in thread title.

---

### Post by CharlesA on 2012-02-27
I've always used the full path to the program that runs the script. I don't think I've actually used #!/usr/bin/env bash before.

Lars covered it. I didn't know Ubuntu used dash instead of bash, but I've written my scripts for bash and they run fine. I guess it all depends on what the script is meant to do and if dash supports it or not.

---

### Post by josephmills on 2012-02-27
wow you guys are awesome thanks I also just read this 
> This header (also called the hashbang or shebang) makes sure that whenever your script is executed, BASH will be used as its interpreter. The way it works, is that when the kernel executes a non-binary, it looks at the first line of the file. If the line begins with #!, the kernel uses the line to determine the interpreter that the code should be passed to. (There are other valid ways to do this, as well -- see below.) The #! must be at the very start of the file, with no spaces or blank lines before them. Your script's commands should all appear on separate lines below this.

Please do not be fooled by examples on the Internet that use /bin/sh as interpreter. sh is not bash. Even though sh's syntax and bash's look very much alike and even though most bash scripts will run in sh, a lot of the examples in this guide only apply to bash and will just break or cause unexpected behaviour in sh.

Also, please refrain from giving your scripts that stupid .sh extension. It serves no purpose, and it's completely misleading (since it's going to be a bash script, not an sh script).



so that is cool then I seen this that expains that whole thing 
> 
Tip: 
You can use this header to specify up to one word of optional arguments that you want to pass to the interpreter. For example, the following arguments will turn on some verbose debugging:
    #! /bin/bash -xv
But that requires knowing where Bash is installed, and it's not always in /bin. Unfortunately, you can't use this:
    #! /usr/bin/env bash -xv
because that would require two words of arguments in the header line. Unix doesn't allow that. You can do this instead:
    #! /usr/bin/env bash
    set -xv

Once again you all are awesome thanks again esp.for fixing the title. thanks 
joseph

---

