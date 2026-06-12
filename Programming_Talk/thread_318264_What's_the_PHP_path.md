---
title: "What's the PHP path?"
date: 2006-12-13
forum: Programming Talk
---

### Post by Zantive on 2006-12-13
I am needing to run PHP scripts from the command line. I have searched endlessly, but I just CANT find where PHP was installed to! I've searched several Apache and PHP-5 folders, but I just can't find the PHP executable? Can somebody point me in the right direction?

---

### Post by marianom on 2006-12-13
According to the help you can query in the configure file when building from source:

```

Usage: configure [options] [host]
Options: [defaults in brackets after descriptions]
Configuration:
  --cache-file=FILE       cache test results in FILE
  --help                  print this message
  --no-create             do not create output files
  --quiet, --silent       do not print `checking...' messages
  --version               print the version of autoconf that created configure
Directory and file names:
  --prefix=PREFIX         install architecture-independent files in PREFIX
                          [/usr/local]
  --exec-prefix=EPREFIX   install architecture-dependent files in EPREFIX
                          [same as prefix]

```


Check usr/local to see if it's there.

---

### Post by jayemef on 2006-12-14
You need the commandline installation:
```

sudo apt-get install php5-cli
# OR
sudo apt-get install php4-cli

```

Hope that helps.

---

