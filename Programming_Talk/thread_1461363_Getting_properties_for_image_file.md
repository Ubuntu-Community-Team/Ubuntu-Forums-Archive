---
title: "Getting properties for image file"
date: 2010-04-24
forum: Programming Talk
---

### Post by jimhenry on 2010-04-24
I'm looking for a way to get the basic properties -- particularly, the height and width in pixels -- of an image file from a shell or Perl script.  E.g., a Perl module that would let me read a file, turn it into an object of some kind, and query its properties; or a command-line program that reads a JPG, PNG, etc. and prints its properties or a specified subset of them to stdout.

---

### Post by Some Penguin on 2010-04-24
[http://www.imagemagick.org/script/perl-magick.php](http://www.imagemagick.org/script/perl-magick.php)

It's overkill, but it'll do what you want.

---

### Post by geirha on 2010-04-24
And for shell scripts there's imagemagick's identify command.

E.g.
```
identify -format "%wx%h" image.png
```

[http://www.imagemagick.org/script/identify.php](http://www.imagemagick.org/script/identify.php)

---

