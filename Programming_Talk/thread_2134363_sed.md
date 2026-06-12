---
title: "sed"
date: 2013-04-11
forum: Programming Talk
---

### Post by pqwoerituytrueiwoq on 2013-04-11
sed is black magic to me, i have edited a sed command i got before, but now i am stuck
```
sed '/^[^#]*ubuntu-software-center.desktop/a \        <Filename>synaptic.desktop</Filename>' /etc/xdg/xdg-xubuntu/menus/xfce-applications.menu

```
how can i limit this to only do it 2 times of 3 possible
if i could limit it to only checking the 1st 50 lines or so that would work also

i tried this but it does not seem work with this sed usage (make it do something weard)
[http://stackoverflow.com/questions/148451/how-to-use-sed-to-replace-only-the-first-occurrence-in-a-file](http://stackoverflow.com/questions/148451/how-to-use-sed-to-replace-only-the-first-occurrence-in-a-file)

edit: i do actually need it 3 times but i would like more leading spaces on the last one

---

### Post by schragge on 2013-04-11
IMO, sed is not the best tool for this, [sgrep]("http://manpages.ubuntu.com/manpages/precise/en/man1/sgrep.1.html") is much better at processing XML. Anyway, try this
```

sed '/<Filename>ubuntu-software-center\.desktop<\/Filename>/{h;s/\(^[ \t]*\).*/\1<Filename>synaptic\.desktop<\/Filename>/;H;g}' /etc/xdg/xdg-xubuntu/menus/xfce-applications.menu

```
It should add *synaptic.desktop* after each occurence of *ubuntu-software-center.desktop* keeping the indentation from the previous line.

---

### Post by Vaphell on 2013-04-11
if sed solution requires buffer swapping voodoo i go straight to awk. It is more verbose but so what - it's 10x more readable, you have variables and can control flow with ease.

```
$ for i in {1..5}; do echo $i pattern; done
1 pattern
2 pattern
3 pattern
4 pattern
5 pattern
$ for i in {1..5}; do echo $i pattern; done | awk 'BEGIN { c=0; }
                                                   /pattern/ && c<2 { c++; gsub(/pattern/,"abc"); }
                                                   { print; }'
1 abc
2 abc
3 pattern
4 pattern
5 pattern
```

---

### Post by Vaphell on 2013-04-11
double post

---

