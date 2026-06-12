---
title: "[SOLVED] Script to run two commands at once"
date: 2008-09-24
forum: New to Ubuntu
---

### Post by askander on 2008-09-24
Hi!

I Installed a program using wine an it runs flawlessly, but to use it, I need to execute a mount instruction in terminal, I know there's a way to make an script that mounts the folder I want and then start the application without touching the terminal, but I don't know how to do it.... any help? :confused:

---

### Post by Paqman on 2008-09-24
[How to write a simple bash script](http://floppix.ccai.com/scripts1.html)

---

### Post by anotherdisciple on 2008-09-24
I rarely use wine, so I can't help you there... but to run two commands at once you need to send them to the background with (&).

This would open gimp and firefox at the same time:
```
firefox &
gimp &
```

This would attempt to delete a file... and if it was sucessful... it will delete anotherfile:

```
sudo rm /path/to/file && sudo rm /path/to/another/file
```

---

### Post by Titan8990 on 2008-09-24
A shell script like that is very easy to make. Scripts always begin with a "shebang" to tell the shell what interpreter to use.

Make a text file in an easy to find directory:

```
#!/bin/bash

COMMAND1
COMMAND2
COMMAND3
```

Use the shebang line that I have given. Replace COMMAND1 and etc with the command you would like the script to run.

Save the text file and then you have to make it executable. For this I will assume that the the file is called "test.sh". To make it executable:

chmod 775 test.sh

Then you can run the script:

./test.sh

Good luck!

---

### Post by anotherdisciple on 2008-09-24
> **Titan8990 said:**
> A shell script like that is very easy to make. Scripts always begin with a "shebang" to tell the shell what interpreter to use.

Make a text file in an easy to find directory:

```
#!/bin/bash

COMMAND1
COMMAND2
COMMAND3
```

Use the shebang line that I have given. Replace COMMAND1 and etc with the command you would like the script to run.

Save the text file and then you have to make it executable. For this I will assume that the the file is called "test.sh". To make it executable:

chmod 775 test.sh

Then you can run the script:

./test.sh

Good luck!

Yes, but the next command can't start until the other command is finished. So, you may need to do this.

```
#!/bin/bash

COMMAND1 &
COMMAND2 &
COMMAND3
```

---

### Post by askander on 2008-09-25
I did it! Thanks all for your help! :)

---

### Post by Titan8990 on 2008-09-25
Good to hear. Don't forget to mark this thread as solved.

---

