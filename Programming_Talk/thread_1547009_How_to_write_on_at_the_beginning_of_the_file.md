---
title: "How to write on at the beginning of the file?"
date: 2010-08-06
forum: Programming Talk
---

### Post by X.Cyclop on 2010-08-06
**echo >>** writes at the end of a file, so is there any way to write at the beginning of a file?

---

### Post by lisati on 2010-08-06
The only way I can think of at the moment is to (a) start a new temporary file, (b) write the stuff you want to insert to the new file, (c) copy the contents of the original file to the new file, (d) delete the original file, and then (e) rename the temporary file as the original file.

---

### Post by cpmman on 2010-08-06
Try ed.

---

### Post by iponeverything on 2010-08-06
The streaming nature of Linux IO does not lend itself to doing this in one step.

```
echo things > tempfile; cat oringalfile >> tempfile; mv tempfile oringalfile
```

---

### Post by X.Cyclop on 2010-08-06
Great, i didn't think about that.
**ed** seems to be a little hard.:)

---

### Post by ghostdog74 on 2010-08-06
```

sed -i.bak '1i text' file

```

---

### Post by interval1066 on 2010-08-06
```

#!/usr/bin/perl
use File::Copy;

$file = "file";
open FILE $file;
print FILE "some text";
copy($file, $file) or die "File cannot be copied.";

```

ghostdog74's way is the best, I just wanted to join the party.

---

### Post by ghostdog74 on 2010-08-06
> **interval1066 said:**
> ```

#!/usr/bin/perl
use File::Copy;

$file = "file";
open FILE $file;
print FILE "some text";
copy($file, $file) or die "File cannot be copied.";

```

ghostdog74's way is the best, I just wanted to join the party.
did you try to run and test your code. ?

---

