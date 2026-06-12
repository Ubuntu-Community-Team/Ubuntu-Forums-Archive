---
title: "create image iso from DVD through command line"
date: 2017-05-19
forum: New to Ubuntu
---

### Post by sed_faster on 2017-05-19
Hello folks,

I was googled and I found this tip:

To create iso image from DVD use this command line:
```

sudo cat /dev/sr0 name_drive_DVD > /path/to/directory/image.iso

```

It is the best way to create a iso from dvd? I intend create a iso from dvd software to windows. But I need this on my environment Linux!

Thanks

---

### Post by SeijiSensei on 2017-05-19
First, if it is a video DVD, chances are that copy-protection will make this difficult.  In that instance I'd use Handbrake.

For a pure data DVD, you can use "dd" like this:
```
dd if=/dev/sr0 of=/path/to/file.iso 
```

---

