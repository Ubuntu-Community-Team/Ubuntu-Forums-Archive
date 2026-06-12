---
title: "My Online Backup Script"
date: 2012-09-30
forum: Programming Talk
---

### Post by huangyingw on 2012-09-30
Hello,
   I have problem at my online backup script for Ubuntu.
   I have added an echo to debug it.
   ```
huangyingw@laptop:~/bashrc$ cat tubak.sh 
#! /bin/bash
UBAKEX=$HOME/bashrc/ubak_ex
UBAKIN=$HOME/bashrc/ubak_in
exclude_params=();
while read suf
do
  exclude_params+=( " --exclude=$suf" )
done < "$UBAKEX"
include_params=();
while read suf
do
  include_params+=( " --include=$suf" )
done < "$UBAKIN"
echo rsync -aHinv --delete-during "${exclude_params[@]}" "${include_params[@]}" / /media/volgrp/media/laptop/

```
   then I run in this way:
   ```
root@laptop:/home/huangyingw# tubak 
rsync -aHinv --delete-during  --exclude=/proc/  --exclude=/media/  --exclude=/sys/  --exclude=myproject  --exclude=/dev/  --exclude=/tmp/  --include=/boot/  --include=/etc/  --include=/home/  --include=/lib/  --include=/root/  --include=/usr/  --include=/var/ / /media/volgrp/media/laptop/

```.
   Then I manually copy the output to run, it is ok.
```
root@laptop:/home/huangyingw# rsync -aHinv --delete-during  --exclude=/proc/  --exclude=/media/  --exclude=/sys/  --exclude=myproject  --exclude=/dev/  --exclude=/tmp/  --include=/boot/  --include=/etc/  --include=/home/  --include=/lib/  --include=/root/  --include=/usr/  --include=/var/ / /media/volgrp/media/laptop/

```
   But, if I remove the echo, to let it run, the exclude, parameter seems does not work, all the staff in /media would be copied.

---

### Post by spjackson on 2012-10-01
I'm not a bash expert and I don't have time to research and test, but since you've had 8 hours without a response, I will share my thoughts.

Since the translated command displayed by echo works correctly when pasted into a terminal but not when executed directly, this suggests to me that the result of substituting "${exclude_params[@]}" is a single word (albeit one containing spaces). If that is the case, then you should have the same problem with the includes as well.

I don't know if this is the best solution, or whether it would actually work, but perhaps it will:
```

echo rsync -aHinv --delete-during $(echo "${exclude_params[@]}") $(echo "${include_params[@]}") / /media/volgrp/media/laptop/

```or maybe simply removing the quotes will do it:
```

echo rsync -aHinv --delete-during ${exclude_params[@]} ${include_params[@]} / /media/volgrp/media/laptop/

```If any of the directories had spaces in their names, you would probably need some extra sophistication (while building the arrays I suspect).

---

### Post by Vaphell on 2012-10-01
> this suggests to me that the result of substituting "${exclude_params[@]}" is a single word (albeit one containing spaces). 

that's not the case, "${array[@]}" expands to separate words. It's easy to check with a for loop.
I'd suspect some sneaky whitespace attached to one of the ends (that double spacing between individual parameters in echo is suspicious) and i would try debugging the problem like this, with printed quotes to make it clear where the parameter boundaries are 
```
$ arr=("/path/1 " /path2 /path3); i=0
$ for x in "${arr[@]}"; do echo $((i++)) "'$x'"; done
0 '/path/1 '
1 '/path2'
2 '/path3'
```

---

### Post by huangyingw on 2012-10-01
> **Vaphell said:**
> that's not the case, "${array[@]}" expands to separate words. It's easy to check with a for loop.
I'd suspect some sneaky whitespace attached to one of the ends (that double spacing between individual parameters in echo is suspicious) and i would try debugging the problem like this, with printed quotes to make it clear where the parameter boundaries are 
```
$ arr=("/path/1 " /path2 /path3); i=0
$ for x in "${arr[@]}"; do echo $((i++)) "'$x'"; done
0 '/path/1 '
1 '/path2'
2 '/path3'
```
I really don't know how comes the double space.
Update the tubak.sh to be ```
huangyingw@laptop:~/bashrc$ cat tubak.sh 
#! /bin/bash
UBAKEX=$HOME/bashrc/ubak_ex
UBAKIN=$HOME/bashrc/ubak_in
exclude_params=();
while read suf
do
  exclude_params+=( " --exclude=$suf" )
done < "$UBAKEX"
include_params=();
while read suf
do
  include_params+=( " --include=$suf" )
done < "$UBAKIN"
for x in "${exclude_params[@]}"; do echo "'$x'"; done
for x in "${include_params[@]}"; do echo "'$x'"; done
echo rsync -aHinv --delete-during "${exclude_params[@]}" "${include_params[@]}" / /media/volgrp/media/laptop
```
And the command output as bellow:```
root@laptop:/home/huangyingw/bashrc# tubak 
' --exclude=/proc/'
' --exclude=/media/'
' --exclude=/sys/'
' --exclude=myproject'
' --exclude=/dev/'
' --exclude=/tmp/'
' --include=/boot/'
' --include=/etc/'
' --include=/home/'
' --include=/lib/'
' --include=/root/'
' --include=/usr/'
' --include=/var/'
rsync -aHinv --delete-during  --exclude=/proc/  --exclude=/media/  --exclude=/sys/  --exclude=myproject  --exclude=/dev/  --exclude=/tmp/  --include=/boot/  --include=/etc/  --include=/home/  --include=/lib/  --include=/root/  --include=/usr/  --include=/var/ / /media/volgrp/media/laptop/
```

---

### Post by Vaphell on 2012-10-01
> I really don't know how comes the double space.

o rly? so what is this? ;-)
```
while read suf
do
  exclude_params+=( "[COLOR="Red"]_[/COLOR]--exclude=$suf" )
done < "$UBAKEX"
```
```
root@laptop:/home/huangyingw/bashrc# tubak 
'[COLOR="Red"]_[/COLOR]--exclude=/proc/'
'[COLOR="Red"]_[/COLOR]--exclude=/media/'
...

```

---

### Post by huangyingw on 2012-10-01
> **Vaphell said:**
> o rly? so what is this? ;-)
```
while read suf
do
  exclude_params+=( "[COLOR="Red"]_[/COLOR]--exclude=$suf" )
done < "$UBAKEX"
```
```
root@laptop:/home/huangyingw/bashrc# tubak 
'[COLOR="Red"]_[/COLOR]--exclude=/proc/'
'[COLOR="Red"]_[/COLOR]--exclude=/media/'
...

```
I know, but the ```
  exclude_params+=( "[COLOR="Red"]_[/COLOR]--exclude=$suf" )
``` will only generate one space, but the final echo has two space between parameters.

---

### Post by Vaphell on 2012-10-01
> but the final echo has two space between parameters.

why would that be? maybe because 1 space was already there by default and you explicitly added another one? ;)


```
$ arr+=("--option1=1"); arr+=("--option2=2")
$ echo "${arr[@]}"
--option1=1 --option2=2
```


Array expansion creates separate words with spaces between them right off the bat. You don't need to help bash with that. '--option' is not the same as ' --option' and no wonder it doesn't work.

tl;dr: remove these spaces in include/exclude_params and enjoy your fancy script ;-)

---

### Post by huangyingw on 2012-10-02
> **Vaphell said:**
> why would that be? maybe because 1 space was already there by default and you explicitly added another one? ;)


```
$ arr+=("--option1=1"); arr+=("--option2=2")
$ echo "${arr[@]}"
--option1=1 --option2=2
```


Array expansion creates separate words with spaces between them right off the bat. You don't need to help bash with that. '--option' is not the same as ' --option' and no wonder it doesn't work.

tl;dr: remove these spaces in include/exclude_params and enjoy your fancy script ;-)

Hey, buddy, as always, more than thanks. Thanks for your guidance step by step.
I am enjoying with my fancy script. From now on, I think I don't need to reboot, and boot a live ubuntu to do backup....

---

