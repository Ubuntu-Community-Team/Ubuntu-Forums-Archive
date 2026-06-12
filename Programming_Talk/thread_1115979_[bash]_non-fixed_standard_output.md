---
title: "[bash] non-fixed standard output"
date: 2009-04-04
forum: Programming Talk
---

### Post by cipher999 on 2009-04-04
I am writing a post-processing script for my video downloads.
This script is ran by sabnzbd who stores the output of the script to put it in history.
Mencoder is part of that script. When I run it from the command line, the output is changing : for each processing frame, it updates it status and the remaining time.
However, when the mencoder output is stored in a file, it is cumulating like this :
```
Pos: 0.0s 2f ( 0%) 0.00fps Trem: 0min 0mb A-V:0.000 [0:0]
Pos: 0.0s 3f ( 0%) 0.00fps Trem: 0min 0mb A-V:0.000 [0:0]
Pos: 0.1s 4f ( 0%) 3.74fps Trem: 0min 0mb A-V:0.000 [0:0]
Pos: 0.1s 5f ( 0%) 4.17fps Trem: 0min 0mb A-V:0.000 [0:0]
Pos: 0.2s 6f ( 0%) 4.60fps Trem: 0min 0mb A-V:0.000 [0:0]
Pos: 0.2s 7f ( 0%) 4.94fps Trem: 0min 0mb A-V:0.000 [0:0]
Pos: 0.3s 8f ( 0%) 5.26fps Trem: 0min 0mb A-V:0.000 [0:0]
Pos: 0.3s 9f ( 0%) 5.53fps Trem: 0min 0mb A-V:0.000 [0:0]
Pos: 0.3s 10f ( 0%) 5.79fps Trem: 0min 0mb A-V:0.000 [0:0]
Pos: 0.4s 11f ( 0%) 6.06fps Trem: 0min 0mb A-V:0.000 [0:0]
Pos: 0.4s 12f ( 0%) 6.29fps Trem: 0min 0mb A-V:0.000 [0:0]
Pos: 0.5s 13f ( 0%) 6.49fps Trem: 0min 0mb A-V:0.000 [0:0]
Pos: 0.5s 14f ( 0%) 6.67fps Trem: 0min 0mb A-V:0.000 [0:0]
Pos: 0.5s 15f ( 0%) 6.85fps Trem: 0min 0mb A-V:0.000 [0:384]
Pos: 0.6s 16f ( 0%) 7.03fps Trem: 0min 0mb A-V:0.000 [0:384]
Pos: 0.6s 17f ( 0%) 7.19fps Trem: 0min 0mb A-V:0.000 [0:384]
```


How do I store only the final output, when mencoder exited, and not all those intermediate lines ?

---

### Post by unutbu on 2009-04-04
Perhaps you can direct the mencoder output to a temporary file like /tmp/mencoder.out
Then run 
```

tail -n 1 /tmp/mencoder.out >> /path/to/script/output
```
to append the last line of /tmp/mencoder.out to your script output.

---

### Post by cipher999 on 2009-04-14
That did the trick, thanks.

---

