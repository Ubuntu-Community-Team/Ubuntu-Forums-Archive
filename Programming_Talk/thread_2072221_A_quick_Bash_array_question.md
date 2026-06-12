---
title: "A quick Bash array question"
date: 2012-10-17
forum: Programming Talk
---

### Post by Intrepid Ibex on 2012-10-17
Just a quick question.

I'm assuming the best/easiest way to do this (using quotes to show the whole thing):

> provides=("java-environment=$_major" "java-runtime=$_major" "java-runtime-headless=$_major" "java-web-start=$_major")
conflicts=("java-environment=$_major" "java-runtime=$_major" "java-runtime-headless=$_major" "java-web-start=$_major" 'java-environment=7' 'java-runtime=7' 'java-runtime-headless=7' 'java-web-start=7')

is with something like (dunno if this works, taken from here: [http://tldp.org/LDP/abs/html/arrays.html](http://tldp.org/LDP/abs/html/arrays.html)):

> provides=("java-environment=$_major" "java-runtime=$_major" "java-runtime-headless=$_major" "java-web-start=$_major")
conflicts=("${provides[@]}" "${provides[@]/#$_major/7}")

If not, then what is?

Thanks.

---

### Post by Vaphell on 2012-10-17
unless there is a _major variable you will get null in place of $_major. Double quotes expand $something to its value. If you want literal $_major you have to use single quotes.

```
$ provides=("java-environment=$_major" "java-runtime=$_major" "java-runtime-headless=$_major" "java-web-start=$_major")
$ for p in "${provides[@]}"; do echo $p; done
java-environment=
java-runtime=
java-runtime-headless=
java-web-start=

$ _major=7
$ provides=("java-environment=$_major" "java-runtime=$_major" "java-runtime-headless=$_major" "java-web-start=$_major")
$ for p in "${provides[@]}"; do echo $p; done
java-environment=7
java-runtime=7
java-runtime-headless=7
java-web-start=7

$ provides=('java-environment=$_major' 'java-runtime=$_major' 'java-runtime-headless=$_major' 'java-web-start=$_major')
$ for p in "${provides[@]}"; do echo $p; done
java-environment=$_major
java-runtime=$_major
java-runtime-headless=$_major
java-web-start=$_major

$ conflicts=("${provides[@]}" "${provides[@]/\$_major/7}") 
$ for c in "${conflicts[@]}"; do echo $c; done
java-environment=$_major
java-runtime=$_major
java-runtime-headless=$_major
java-web-start=$_major
java-environment=7
java-runtime=7
java-runtime-headless=7
java-web-start=7
```

you can also append elements to array which can be used to create cleaner, maintainable code
```
$ params=( web-start environment runtime runtime-headless )
$ provides=()
$ for p in "${params[@]}"; do provides+=( java-$p='$_major' ); done
$ for p in "${provides[@]}"; do echo $p; done
java-web-start=$_major
java-environment=$_major
java-runtime=$_major
java-runtime-headless=$_major
```

---

### Post by Intrepid Ibex on 2012-10-17
Yeah, I was talking about this: [https://aur.archlinux.org/packages/jd/jdk-devel/PKGBUILD](https://aur.archlinux.org/packages/jd/jdk-devel/PKGBUILD).

PKGBUILDs are package scripts for Arch's package manager Pacman.

So am I to understand this will work?:
```
(_major=8)
[...]
provides=("java-environment=$_major" "java-runtime=$_major" "java-runtime-headless=$_major" "java-web-start=$_major")
conflicts=("${provides[@]}" "${provides[@]/\$_major/7}")

```

---

### Post by Vaphell on 2012-10-17
in that code $_major is an actual variable not a literal string, so $ sign shouldn't be escaped

besides its not that hard to see what the array contains, just open terminal and copy paste relevant lines to test ;-)

```
$ _major=8
$ provides=("java-environment=$_major" "java-runtime=$_major" "java-runtime-headless=$_major" "java-web-start=$_major")
$ conflicts=("${provides[@]}" 'java-environment=7' 'java-runtime=7' 'java-runtime-headless=7' 'java-web-start=7')
$ echo ${conflicts[@]}
java-environment=8 java-runtime=8 java-runtime-headless=8 java-web-start=8 java-environment=7 java-runtime=7 java-runtime-headless=7 java-web-start=7
$ conflicts=("${provides[@]}" "${provides[@]/$_major/7}")
$ echo ${conflicts[@]}
java-environment=8 java-runtime=8 java-runtime-headless=8 java-web-start=8 java-environment=7 java-runtime=7 java-runtime-headless=7 java-web-start=7

```

on a sidenote is that correct? conflicts and provides having the same values?

---

### Post by Intrepid Ibex on 2012-10-17
> **Vaphell said:**
> in that code $_major is an actual variable not a literal string, so $ sign shouldn't be escaped

besides its not that hard to see what the array contains, just open terminal and copy paste relevant lines to test ;-)

Yeah I was on Windows and have no interest in installing things like Bash there so that's why I asked, if you could verify for me. That was the reason I wasn't sure.

> **Vaphell said:**
> on a sidenote is that correct? conflicts and provides having the same values?
Well, I don't necessarily know a lot about _Bash_ but it is :). 

It needs to conflict with what it provides (doesn't mean it conflicts with _itself_ it just conflicts with others providing the _same thing_). In addition it has to conflict with JRE/JDK 7, since I grew tired of trying to make it coexist alongside them. The one who uploaded [jre6](https://aur.archlinux.org/packages.php?ID=51909) actually made it so (dunno if it actually works) and started complaining when I was just conflicting with _all_ the java packages when he was just installing into his own separate directory.

Thanks for your help anyway. Hugely.

---

