---
title: "mv all files from the folder to the current position"
date: 2017-08-16
forum: New to Ubuntu
---

### Post by sed_faster on 2017-08-16
Hello folks,

I intend mv all folder and files from folder to the current directory. For example:

```

git clone https://github.com/twbs/bootstrap.git
tree -La 2
.
&#9492;&#9472;&#9472; bootstrap
    &#9500;&#9472;&#9472; assets
    &#9500;&#9472;&#9472; .babelrc
    &#9500;&#9472;&#9472; bower.json
    &#9500;&#9472;&#9472; build
    &#9500;&#9472;&#9472; CNAME
    &#9500;&#9472;&#9472; composer.json
    &#9500;&#9472;&#9472; _config.yml
    &#9500;&#9472;&#9472; _data
    &#9500;&#9472;&#9472; dist
    &#9500;&#9472;&#9472; docs
    &#9500;&#9472;&#9472; .editorconfig
    &#9500;&#9472;&#9472; .eslintignore
    &#9500;&#9472;&#9472; favicon.ico
    &#9500;&#9472;&#9472; Gemfile
    &#9500;&#9472;&#9472; Gemfile.lock
    &#9500;&#9472;&#9472; .git
    &#9500;&#9472;&#9472; .gitattributes
    &#9500;&#9472;&#9472; .github
    &#9500;&#9472;&#9472; .gitignore
    &#9500;&#9472;&#9472; Gruntfile.js
    &#9500;&#9472;&#9472; .houndignore
    &#9500;&#9472;&#9472; .hound.yml
    &#9500;&#9472;&#9472; _includes
    &#9500;&#9472;&#9472; index.html
    &#9500;&#9472;&#9472; js
    &#9500;&#9472;&#9472; _layouts
    &#9500;&#9472;&#9472; LICENSE
    &#9500;&#9472;&#9472; nuget
    &#9500;&#9472;&#9472; package.js
    &#9500;&#9472;&#9472; package.json
    &#9500;&#9472;&#9472; package-lock.json
    &#9500;&#9472;&#9472; _plugins
    &#9500;&#9472;&#9472; README.md
    &#9500;&#9472;&#9472; robots.txt
    &#9500;&#9472;&#9472; sache.json
    &#9500;&#9472;&#9472; scss
    &#9500;&#9472;&#9472; .scss-lint.yml
    &#9500;&#9472;&#9472; sw.js
    &#9492;&#9472;&#9472; .travis.yml

14 directories, 26 files

```

If I want **mv** all files and hidden directory to the current position how should I do? I tested this command, but I doens't always work:
```

xxx@xxxxxx:~/Documents/folder2/folder$ ls -a bootstrap/
.           composer.json  favicon.ico     Gruntfile.js  LICENSE            robots.txt
..          _config.yml    Gemfile         .houndignore  nuget              sache.json
assets      _data          Gemfile.lock    .hound.yml    package.js         scss
.babelrc    dist           .git            _includes     package.json       .scss-lint.yml
bower.json  docs           .gitattributes  index.html    package-lock.json  sw.js
build       .editorconfig  .github         js            _plugins           .travis.yml
CNAME       .eslintignore  .gitignore      _layouts      README.md
xxx@xxxxxx:~/Documents/folder2/folder$ mv bootstrap/* .
xxx@xxxxxx:~/Documents/folder2/folder$ ls -a bootstrap/
.   .babelrc       .eslintignore  .gitattributes  .gitignore    .hound.yml      .travis.yml
..  .editorconfig  .git           .github         .houndignore  .scss-lint.yml
xxx@xxxxxx:~/Documents/folder2/folder$ ls
assets      composer.json  favicon.ico   index.html  package.js         robots.txt
bootstrap   _config.yml    Gemfile       js          package.json       sache.json
bower.json  _data          Gemfile.lock  _layouts    package-lock.json  scss
build       dist           Gruntfile.js  LICENSE     _plugins           sw.js
CNAME       docs           _includes     nuget       README.md
xxx@xxxxxx:~/Documents/folder2/folder$ mv bootstrap/.* .
mv: cannot move 'bootstrap/.' to './.': Device or resource busy
mv: cannot move 'bootstrap/..' to './..': Device or resource busy
xxx@xxxxxx:~/Documents/folder2/folder$ ls -a bootstrap/
..

```

This is the best way?
Thanks

---

### Post by Andreyshel on 2017-08-16
> mv: cannot move 'bootstrap/.' to './.': Device or resource busy


This should not affect moving process. Have you checked if files actually moved?

---

### Post by sed_faster on 2017-08-16
Don't work:
```

xxx@xxxxxx:~/Documents/folder1/teste$ ls -la
total 12
drwxrwxr-x  3 xxx xxx 4096 ago 16 10:10 .
drwxrwxr-x  8 xxx xxx 4096 ago 16 10:05 ..
drwxrwxr-x 15 xxx xxx 4096 ago 16 10:10 bootstrap
xxx@xxxxxx:~/Documents/folder1/teste$ cd bootstrap/ && mv * ..
xxx@xxxxxx:~/Documents/folder1/teste/bootstrap$ ls -la
total 132
drwxrwxr-x  4 xxx xxx  4096 ago 16 10:13 .
drwxrwxr-x 14 xxx xxx  4096 ago 16 10:13 ..
-rw-rw-r--  1 xxx xxx   172 ago 16 10:10 .babelrc
-rw-rw-r--  1 xxx xxx   232 ago 16 10:10 .editorconfig
-rw-rw-r--  1 xxx xxx    34 ago 16 10:10 .eslintignore
drwxrwxr-x  8 xxx xxx  4096 ago 16 10:10 .git
-rw-rw-r--  1 xxx xxx   359 ago 16 10:10 .gitattributes
drwxrwxr-x  2 xxx xxx  4096 ago 16 10:10 .github
-rw-rw-r--  1 xxx xxx   551 ago 16 10:10 .gitignore
-rw-rw-r--  1 xxx xxx    45 ago 16 10:10 .houndignore
-rw-rw-r--  1 xxx xxx   182 ago 16 10:10 .hound.yml
-rw-rw-r--  1 xxx xxx 12105 ago 16 10:10 .scss-lint.yml
-rw-rw-r--  1 xxx xxx   904 ago 16 10:10 .travis.yml
xxx@xxxxxx:~/Documents/folder1/teste/bootstrap$ cd ..
xxx@xxxxxx:~/Documents/folder1/teste$ ls -la
total 488
drwxrwxr-x 14 xxx xxx   4096 ago 16 10:13 .
drwxrwxr-x  8 xxx xxx   4096 ago 16 10:05 ..
drwxrwxr-x  7 xxx xxx   4096 ago 16 10:10 assets
drwxrwxr-x  4 xxx xxx   4096 ago 16 10:13 bootstrap
-rw-rw-r--  1 xxx xxx    679 ago 16 10:10 bower.json
drwxrwxr-x  2 xxx xxx   4096 ago 16 10:10 build
-rw-rw-r--  1 xxx xxx     26 ago 16 10:10 CNAME
-rw-rw-r--  1 xxx xxx    744 ago 16 10:10 composer.json
-rw-rw-r--  1 xxx xxx   2385 ago 16 10:10 _config.yml
drwxrwxr-x  2 xxx xxx   4096 ago 16 10:10 _data
drwxrwxr-x  4 xxx xxx   4096 ago 16 10:10 dist
drwxrwxr-x  3 xxx xxx   4096 ago 16 10:10 docs
-rw-rw-r--  1 xxx xxx   5430 ago 16 10:10 favicon.ico
-rw-rw-r--  1 xxx xxx    235 ago 16 10:10 Gemfile
-rw-rw-r--  1 xxx xxx   1557 ago 16 10:10 Gemfile.lock
-rw-rw-r--  1 xxx xxx    719 ago 16 10:10 Gruntfile.js
drwxrwxr-x  3 xxx xxx   4096 ago 16 10:10 _includes
-rw-rw-r--  1 xxx xxx   4410 ago 16 10:10 index.html
drwxrwxr-x  5 xxx xxx   4096 ago 16 10:10 js
drwxrwxr-x  2 xxx xxx   4096 ago 16 10:10 _layouts
-rw-rw-r--  1 xxx xxx   1131 ago 16 10:10 LICENSE
drwxrwxr-x  2 xxx xxx   4096 ago 16 10:10 nuget
-rw-rw-r--  1 xxx xxx    535 ago 16 10:10 package.js
-rw-rw-r--  1 xxx xxx   6565 ago 16 10:10 package.json
-rw-rw-r--  1 xxx xxx 214417 ago 16 10:10 package-lock.json
drwxrwxr-x  2 xxx xxx   4096 ago 16 10:10 _plugins
-rw-rw-r--  1 xxx xxx   8443 ago 16 10:10 README.md
-rw-rw-r--  1 xxx xxx    123 ago 16 10:10 robots.txt
-rw-rw-r--  1 xxx xxx    249 ago 16 10:10 sache.json
drwxrwxr-x  4 xxx xxx   4096 ago 16 10:10 scss
-rw-rw-r--  1 xxx xxx     17 ago 16 10:10 sw.js

```

---

### Post by Andreyshel on 2017-08-16
Your files are hidden. Do not forget to run mv .* ..  too

---

### Post by sed_faster on 2017-08-16
Ok, but which the difference between your code and my code?
Maybe shouldn't have difference, because exist many ways to solve the problem ;)

However, why do you edited your answer?

---

### Post by mc4man on 2017-08-16
I suspect from your orig. position you could of just gone
```
 mv */* */.* .
```

---

### Post by Andreyshel on 2017-08-16
Yes but maybe 
```
mv bootstrap/* bootstrap/.* .
```
better , because there  can be some other folders which will be extracted too if you write * as a first symbol.

---

### Post by sisco311 on 2017-08-16
> **Edgar_Oliveira said:**
> 
This is the best way?


If it works is a good way.  You get the errors because .* matches . and .. which are hard links to the current and parent directories.


In bash you can use the dotglob option:
```
shopt -s dotglob
mv bootstrap/* ./
shopt -u dotglob
```

You can also use some globs to match any file but . and .. or you can use find. The web is full with examples.

---

### Post by vocx on 2017-08-16
> **mc4man said:**
> I suspect from your orig. position you could of just gone
```
 mv */* */.* .
```
It's "could have" not "could of".

The command "mv" has a switch to specifically define the target directory to where you want the files moved. Maybe it's a bit counter intuitive but the directory is placed first, and the rest of the arguments are the files or directories moved.

```

# move all files inside the bootstrap directory to the present directory
mv -t . bootstrap/*

# move all files inside the bootstrap directory to the parent of the present directory
mv -t .. bootstrap/*

```

```

# move all files inside the bootstrap directory, and "whatever", "blafile", and "dfsdfl"
# to the directory "/blabla" which is the first argument after the -t
mv -t /blabla bootstrap/* /var/whatever /some/blafile /temp/dfsdfl

```

---

