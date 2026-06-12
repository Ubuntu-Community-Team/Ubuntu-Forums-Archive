---
title: "Convert number range to individual numbers."
date: 2009-07-07
forum: Programming Talk
---

### Post by kaibob on 2009-07-07
I have a few scripts that obtain a series of page numbers with a zenity dialog. These often include both individual numbers and number ranges. An example is: 

1 2 4-6 8-10

I need to convert the above into individual numbers only, as in the following:

1 2 4 5 6 8 9 10

I wrote the code included below, which does the job, but I wondered if there might be some utility (similar to seq) that will do the job more directly. As an alternative, can awk calculate the individual numbers (i.e. convert 4-6 to 4 5 6). This would make seq unnecessary. 

Thanks.

```
#!/bin/bash

numbers=( 1 2 4-6 8-10 ) # Normally comes from zenity dialog. 

for number in ${numbers[@]} ; do
	range=$(echo "$number" | awk -F "-" '/-/ { print $1 " " $2 }')
	[ "${range}" ] && newnumbers=( "${newnumbers[@]}" $(seq $range ))
	[ "${range}" ] || newnumbers=( "${newnumbers[@]}" "$number" )
done

echo ${newnumbers[@]} # Check to see if this works OK.
```

---

### Post by ghostdog74 on 2009-07-07
> **kaibob said:**
>  can awk calculate the individual numbers (i.e. convert 4-6 to 4 5 6). 
Of course it can. It will mostly involve loops. Remember, awk is also a small programming language by itself. it can do mostly what bash can do. Here's an example done with only awk.
```

echo "1 2 4-6 8-10 11-20 21" | awk '
{
 for(i=1;i<=NF;i++){
    if( $i ~ /-/){
        m=split($i,a,"-")
        if (m==2){
            for(o=a[1];o<=a[2];o++){
                printf "%d ", o
            }
            print ""
        }
    }else{
        print $i
    }
 }
}'


```
output
```

# ./test.sh
1
2
4 5 6
8 9 10
11 12 13 14 15 16 17 18 19 20
21


```

---

### Post by kaibob on 2009-07-07
Thanks for the response ghostdog74. I've been working to learn awk, but thus far have only mastered simple one-liners, and the code you wrote is beyond my ability to understand or maintain.

If I could ask a question, which you have in a sense already answered, but it's buried within code that I do not understand. I need something that checks to see if the piped value contains a dash and if so to expand the range into individual values. The following doesn't work, but I think it conveys the idea. It should assign "5 6 7 8 9 10" (no quotes) to $range. 

```
range=(echo "5-10" | awk -F "-" '/-/ {for(i=$1;i<=$2;i++){print $i}}')
```

Thanks again for the help.

---

### Post by ghostdog74 on 2009-07-07
> **kaibob said:**
> 

```
range=(echo "5-10" | awk -F "-" '/-/ {for(i=$1;i<=$2;i++){print $i}}')
```

Thanks again for the help.
```

for(i=$1;i<=$2;i++)

```
this is your problem. you are printing $i and not i. you should print i instead of $i. also, you want to get everything to one line, use printf

---

### Post by kaibob on 2009-07-07
> **ghostdog74 said:**
> ...this is your problem. you are printing $i and not i. you should print i instead of $i. also, you want to get everything to one line, use printf

Thanks. That works great.

```
#!/bin/bash

numbers=( 1 2 4-6 8-10 ) # Normally comes from zenity dialog. 

for number in ${numbers[@]} ; do
	range=$(echo "$number" | awk -F "-" '/-/ {for (i=$1 ; i<=$2 ; i++) {printf i " "}}')
	[ "${range}" ] && newnumbers=( "${newnumbers[@]}" "$range" )
	[ "${range}" ] || newnumbers=( "${newnumbers[@]}" "$number" )
done

echo ${newnumbers[@]} # Check to see if this works OK.
```

---

### Post by stroyan on 2009-07-08
You can do this with just bash if you like.
Here is an example that uses several bash constructs.
case is used to identify the lines with numbers and with ranges.
a+=( values) is used to assign one or more values to the end of an array.
${var/from/to} is used to replace a - in a range with .. .
Range notation like {4..6} is used to evaluate each range.
eval is used to turn {4..6} into 4 5 6 before assigning to an array.

```

#!/bin/bash

numbers=( 1 2 4-6 8-10 ) # Normally comes from zenity dialog. 

unset newnumbers[@];
shopt -s extglob # allow +() in regular expression
for number in ${numbers[@]} ; do
        case "$number" in
                +([[:digit:]]) )
                        newnumbers+=( $number )
                        ;;
                +([[:digit:]])-+([[:digit:]]) )
                        eval newnumbers+=( {${number/-/..}} )
                        ;;
        esac
done

echo ${newnumbers[@]} # Check to see if this works OK.

```

---

### Post by bigboy_pdb on 2009-07-08
I don't see why you need awk for that since it can be done using the bash shell. You can make your own utility. If you paste the code below into a file called "sequence" and use the command "chmod 755 sequence", you'll be able to pass in arguments using the command line (ie. "sequence 1 2 3-5 6" will output "1 2 3 4 5 6").

```

#!/bin/bash

while (( $# > 0 )); do
        if grep -q '[[:digit:]]\+-[[:digit:]]\+' <<< "$1"; then
                echo -n $(seq $(sed 's/-/ /' <<< "$1"))' '
        elif grep -q '[[:digit:]]\+' <<< "$1"; then
                echo -n "$1 "
        fi

        shift;
done
echo ''

```

---

### Post by ghostdog74 on 2009-07-08
> **bigboy_pdb said:**
> I don't see why you need awk for that since it can be done using the bash shell. 
then why are you using grep? its not part of bash shell. awk is a better utility/tool than the bash shell to process text/file. Period.

---

### Post by kaibob on 2009-07-08
Thanks everyone for the responses. I appreciate the help.

@Stroyan. I've been working hard to learn bash but found a lot of new stuff in your shell script. Thanks for the post.

---

### Post by bapoumba on 2009-07-08
Closing the thread per OP's request.
Two posts moved out to recurring : [http://ubuntuforums.org/showthread.php?t=1207768](http://ubuntuforums.org/showthread.php?t=1207768)

---

