---
title: "help explain simple oneliner perl program"
date: 2008-12-27
forum: Programming Talk
---

### Post by monkeyking on 2008-12-27
I trying to install a program,
and then the guide tells me to

```

sudo perl -pi -w -e ’s/!\/bin\/sh/!\/bin\/bash/g;’ *

```

somethings thats /bi/sh should be /bin/bash,
I've gotten this far.
But the ticks are the wrong, way right?
And this perl script should be run on all files in the current directory right?


thank in advance

---

### Post by eightmillion on 2008-12-27
I think you've pretty much got it figured out. This one liner just changes all the hash bangs in all the files in a directory from #!/bin/sh to #!/bin/bash. The quotes are wrong. You'll have to change it to:

```
sudo perl -pi -w -e 's/!\/bin\/sh/!\/bin\/bash/g;' *

```

---

