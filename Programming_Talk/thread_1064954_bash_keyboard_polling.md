---
title: "bash keyboard polling"
date: 2009-02-09
forum: Programming Talk
---

### Post by jleems86 on 2009-02-09
hi all, i have a question.
I'm running a bash script in the background and need to change behavior based on when certain keys are pressed. 
I have to poll the output of showkey so that my script only responds when a certain key is pressed.  the problem is i have no idea how to implement this.

  
Details: this is a script that is going to be running in the background on google android (I'm using the getevent command instead of showkey, but same behavior, also have busybox installed to help)

ultimately, this is to run in the background, continually polling getevent (which acts like showkey for the non-keyboard buttons) and activates a second script only when a certain button is pressed.

i think i need a while loop but I'm not really sure how to set this up

---

### Post by Yuzem on 2009-02-17
To get the keys from the terminal you have to do this:
```

while true ; do
   read -n1 key
   echo you pressed the $key key
done
```

---

