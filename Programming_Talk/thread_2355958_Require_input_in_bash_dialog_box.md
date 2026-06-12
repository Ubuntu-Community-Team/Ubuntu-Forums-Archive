---
title: "Require input in bash dialog box"
date: 2017-03-18
forum: Programming Talk
---

### Post by woodson2 on 2017-03-18
Hello.


Any help would be greatly appreciated.


Right now I have the following input box that works fine and well, however I would like to wrap this is a loop that requires input. Right now the script will happily continue on if the user just hits enter. I'd like to require a minimum of a 5 digit number or n/a or N/A as the only viable options otherwise you should get prompted to re-enter information.


```



DIALOG=${DIALOG=dialog}
$DIALOG --title "RFC NUMBER" --clear \
        --inputbox "Please enter an RFC Number" 16 17 2> $rfcfile


retval=$?
rfcval=`cat $rfcfile`


case $retval in
  0)
    echo RFC Number: "$rfcval" >> $accessfile;;
  1)
    exit 1;;
  255)
    rm -rf $accessfile && rm -rf $tempfile && rm -rf $rfcfile && rm -rf $sitefile && exit 1;;
  esac



```

---

