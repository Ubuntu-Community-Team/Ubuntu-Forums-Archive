---
title: "Bash - Can't read variable from inside of while loop"
date: 2009-03-10
forum: Programming Talk
---

### Post by u-slayer on 2009-03-10
```
l1=en,sv
l2=fr,en,es
echo "$l1" | sed 's/,/\n/g' |
while read lineA; do
	echo "$l2" | sed 's/,/\n/g' |
	while read lineB; do
		echo "a = $lineA - b = $lineB"
		if [ "$lineA" == "$lineB" ]; then
			out=$out$lineB
			echo "Inner Out = $out"
		fi
	done
done
		
echo "Out = $out"
```

I wrote some code to compare comma separated lists and output the differences. But I can't get variable inside the loop to keep their data outside the loop. It's very frustrating.

---

### Post by ghostdog74 on 2009-03-10
```

# a=fr,en,es
# b=en,es,fr
# ra=`echo $a | tr "," "\n" |sort`
# rb=`echo $b | tr "," "\n" |sort`
# if [ "$ra" == "$rb" ];then echo 'yes'; fi
yes


```

---

### Post by croto on 2009-03-10
the problem is that after the pipe, the following bash commands are being executed in a subshell - another instance of bash. When that subinstance exits, the parent has no idea about the variables the subshell instantiated. I'd try to have everything running in the same shell. I rewriten your code without that nasty pipeline:
```

l1=en,sv
l2=fr,en,es

l1=$(echo $l1 | tr , ' ')
l2=$(echo $l2 | tr , ' ')
for lineA in $l1; do
	for lineB in $l2; do
		echo "a = $lineA - b = $lineB"
		if [ "$lineA" == "$lineB" ]; then
			out=$out$lineB
			echo "Inner Out = $out"
		fi
	done
done
		
echo "Out = $out"

```

I think it's doing the same as your code... too sleepy to test.

---

### Post by eightmillion on 2009-03-10
I would just add that if you're intent on using while loops, you can use process substitution to pass the output of those commands to your loops. This is effectively the same as passing a file to the loops. The loops end up running in the same shell.

[PHP]
#!/bin/bash
l1=en,sv
l2=fr,en,es
while read lineA; do
        while read lineB; do
                echo "a = $lineA - b = $lineB"
                if [ "$lineA" == "$lineB" ]; then
                        out=$out$lineB
                        echo "Inner Out = $out"
                fi
        done < <(echo "$l2" | sed 's/,/\n/g')
done < <(echo "$l1" | sed 's/,/\n/g')
echo "Out = $out"
[/PHP]

Output:
```
a = en - b = fr
a = en - b = en
Inner Out = en
a = en - b = es
a = sv - b = fr
a = sv - b = en
a = sv - b = es
Out = en
```

---

### Post by u-slayer on 2009-03-11
Thanks for the replies guys - but I went the easy way. I just embedded some python code in my bash to handle situations with funky math or regular expressions. It works much nicer now.

---

