---
title: "Bash beep not working"
date: 2013-11-01
forum: Programming Talk
---

### Post by florin011 on 2013-11-01
Hello! I'm trying to have a beep sound from a bash script.

```

#!/bin/bash
#echo -e "\a"
#echo ^G
echo -en "\007"

```

I modified the /etc/modprobe.d/blacklist.conf file so now I have:
```

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
#blacklist pcspkr

```

What can I do to solve this?

---

### Post by sudodus on 2013-11-03
Welcome to the Ubuntu Forums :-)

See this link [http://ubuntuforums.org/showthread.php?t=2179598](http://ubuntuforums.org/showthread.php?t=2179598) to get ***beep***

and [http://ubuntuforums.org/showthread.php?t=2096908](http://ubuntuforums.org/showthread.php?t=2096908) to get ***espeak***

---

