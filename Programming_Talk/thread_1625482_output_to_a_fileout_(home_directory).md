---
title: "output to a fileout (home directory)"
date: 2010-11-19
forum: Programming Talk
---

### Post by ibizatunes on 2010-11-19
```
'du -sk /home/* | sort -n | perl -ne '\''($s,$f)=split(m{\t});for (qw(K M G)) {if($s<1024) {printf("%.1f",$s);print "$_\t$f"; last};$s=$s/1024}'\' | >> /tmp/file_useage
```

I need this to output to a file, as i want all home directory listed in size but it a text file

I know this work if I alias it (which is the way i have been working out previously for admin work but i need to extract it for a manager and it need to be a text file

```
alias duf='du -sk /home/* | sort -n | perl -ne '\''($s,$f)=split(m{\t});for (qw(K M G)) {if($s<1024) {printf("%.1f",$s);print "$_\t$f"; last};$s=$s/1024}'\'
```

---

### Post by MadCow108 on 2010-11-19
the pipe at the end is wrong when you want to output into a file:
```

...4}'\' | >> /tmp/file_useage
remove   ^ this

```

---

### Post by ibizatunes on 2010-11-19
tried that get this instead
-bash: du -sk /home/* | sort -n | perl -ne '($s,$f)=split(m{\t});for (qw(K M G)) {if($s<1024) {printf("%.1f",$s);print "$_\t$f"; last};$s=$s/1024}': No such file or directory
Any more ideas?

---

### Post by ibizatunes on 2010-11-19
Fixed it.... a cup of tea and clear head!!
```
alias duf='du -sk /home/* | sort -n | perl -ne '\''($s,$f)=split(m{\t});for (qw(K M G)) {if($s<1024) {printf("%.1f",$s);print "$_\t$f"; last};$s=$s/1024}'\' | duf >> /tmp/file_useage
```
just pipe alias duf out to a file :-)

---

### Post by DaithiF on 2010-11-19
> **ibizatunes said:**
> Fixed it.... a cup of tea and clear head!!
```
alias duf='du -sk /home/* | sort -n | perl -ne '\''($s,$f)=split(m{\t});for (qw(K M G)) {if($s<1024) {printf("%.1f",$s);print "$_\t$f"; last};$s=$s/1024}'\' | duf >> /tmp/file_useage
```just pipe alias duf out to a file :-)

this makes no sense to me.

Either:
(a) you define your alias to generate results to std out, and then when wishing to save the results you execute the alias with a redirection, e.g:
```
$ alias duf='du -sk /home/* | sort -n | perl -ne '\''($s,$f)=split(m{\t});for (qw(K M G)) {if($s<1024) {printf("%.1f",$s);print "$_\t$f"; last};$s=$s/1024}'\'
$ duf > /path/to/some/file
```

(b) Or, you define your alias with redirection to a file builtin, so that you just execute the alias.
```
$ alias duf='du -sk /home/* | sort -n | perl -ne '\''($s,$f)=split(m{\t});for (qw(K M G)) {if($s<1024) {printf("%.1f",$s);print "$_\t$f"; last};$s=$s/1024}'\'' > /path/to/some/file'
$ duf

```

you probably want > redirection rather than >> since with >> you will append results to the file each time rather than replacing what was previously there.

---

