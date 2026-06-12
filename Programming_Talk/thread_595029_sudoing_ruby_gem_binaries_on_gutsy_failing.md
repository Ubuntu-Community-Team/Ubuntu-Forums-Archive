---
title: "sudoing ruby gem binaries on gutsy failing"
date: 2007-10-28
forum: Programming Talk
---

### Post by polypus on 2007-10-28
hi all,

i'm running gutsy and have the rubygems package installed. if i try to 'sudo rake blah', or for that matter 'sudo cmd args', where cmd is any program under /var/lib/gems/1.8/bin i get 'sudo: rake: command not found'. if i say 'sudo echo $PATH' i get '~/bin:/var/lib/gems/1.8/bin:blah/blah/blah'

so what's up? any ideas? where is the global path set in gutsy?

thanks,
_c

---

### Post by sciurus on 2007-10-28
a better test is to create a shell script like
```
#!/bin/sh
echo $PATH
```

Run that as sudo and you'll see that the path doesn't include the gems. I beleive changing the path is considered a security feature, for why see [http://www.kramse.dk/projects/unix/security-sudo-script_en.html](http://www.kramse.dk/projects/unix/security-sudo-script_en.html). You can alter the path for all  bash shells through /etc/bash.bashrc. I'm not certain this is the best way.

---

### Post by polypus on 2007-10-28
hi thanks,

i tried that, i put

export PATH="$PATH:/var/lib/gems/1.8/bin/"

in /etc/bash.bashrc at the bottom of the file. logged out an back in and still when i run the script you indicated, it does not include my new path.

any ideas?

thanks,
_c

---

