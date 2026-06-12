---
title: "need help: force script exit on long process"
date: 2012-03-02
forum: Programming Talk
---

### Post by xzero1 on 2012-03-02
Why doesn't this script exit early? I know I will still need to kill the ffmpeg process.

```

#!/bin/bash
function check () {
  sleep 5
  killall ffmpeg
  exit 1
}

check & ffmpeg...     #(long conversion here)
exit 0

```

Nevermind the script does work, I have simplified the example too much.

---

