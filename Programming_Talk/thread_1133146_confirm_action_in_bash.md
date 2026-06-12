---
title: "confirm action in bash"
date: 2009-04-22
forum: Programming Talk
---

### Post by wesg on 2009-04-22
Most scripts require some kind of confirmation that the action has completed successfully. When I would code in PHP, nearly every function was able to return a "true" boolean when completed. Is there an equivalent statement in Bash?

My specific example is that I am converting files with ffmpeg and would like to delete the originals after they have been transcoded. I'm not sure how to check if the file is finished though, so if it actually fails, then I delete the original. Preferably, I'd like a solution that works with other functions as well.

---

### Post by MadCow108 on 2009-04-22
the $? variable holds the returncode of the last executed command.
So if the command executed returns something different depending on failure or not you can use it.

[http://tldp.org/LDP/abs/html/exit-status.html](http://tldp.org/LDP/abs/html/exit-status.html)

---

### Post by wesg on 2009-04-22
Ah yes, thank you MadCow, this will be very useful.

---

