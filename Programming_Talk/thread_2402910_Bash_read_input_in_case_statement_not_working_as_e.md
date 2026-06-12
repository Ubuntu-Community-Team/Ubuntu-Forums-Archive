---
title: "Bash read input in case statement not working as expected"
date: 2018-10-05
forum: Programming Talk
---

### Post by woodson2 on 2018-10-05
I'm having an issue with bash read input when using a case statement.


The script halts and doesn't read the input on the first loop. if I hit enter then the scripts starts to respond as expected. Need some help here.


```
defaultans=8hrs
read -e -i $defaultans -p "${bldwht}How long would you like to grant access to $USERNAME (8hrs,24hrs,48hrs,72hrs,96hrs,1wk or 2wk)? ${txtrst}" input
defaultans="${input:-$defaultans}"
#echo -e "${bldwht}How long would you like to grant access to $USERNAME (8hrs,24hrs,48hrs,72hrs,96hrs,1wk or 2wk)? ${txtrst}"
       echo "       "
        echo "       "
while true; do
read defaultans
case $defaultans in
     8hrs ) break;;
     24hrs ) break;;
     48hrs ) break;;
     72hrs ) break;;
     96hrs ) break;;
       1wk ) break;;
       2wk ) break;;
     * ) echo "You entered an invalid choice. You must choose 8hrs,24hrs,48hrs,72hrs,96hrs,1wk or 2wk access.";;
    esac
done

```








Script output in debug.


+ defaultans=8hrs
+ read -e -i 8hrs -p 'How long would you like to grant access to tnew (8hrs,24hrs,48hrs,72hrs,96hrs,1wk or 2wk)? ' input
How long would you like to grant access to tnew (8hrs,24hrs,48hrs,72hrs,96hrs,1wk or 2wk)? 8hrs
+ defaultans=8hrs
+ echo '       '


+ echo '       '


+ true
[B]+ read defaultans  < script sits here and doesn't read the given defaultans above.
[/B]


[B][U]##Once I hit enter one time the script proceeds as expected.
[/U][/B]+ case $defaultans in
+ echo 'You entered an invalid choice. You must choose 8hrs,24hrs,48hrs,72hrs,96hrs,1wk or 2wk access.'
You entered an invalid choice. You must choose 8hrs,24hrs,48hrs,72hrs,96hrs,1wk or 2wk access.
+ true
+ read defaultans

---

### Post by TheFu on 2018-10-05
Best to check the ABSG for details.  [https://www.tldp.org/LDP/abs/html/testbranch.html#EX29](https://www.tldp.org/LDP/abs/html/testbranch.html#EX29)

I always use getopts and functions myself.
```
# ###########################################################
while getopts 'lh?' OPTION
do
  case $OPTION in
  l)    show_license
        ;;
  h)    show_usage
        ;;
  ?)    show_usage
        ;;
  esac
done

```

And if you are in a loop, might want to shift.

---

