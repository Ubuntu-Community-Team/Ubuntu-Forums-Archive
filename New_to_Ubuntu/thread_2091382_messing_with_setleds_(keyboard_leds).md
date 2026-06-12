---
title: "messing with setleds? (keyboard leds)"
date: 2012-12-05
forum: New to Ubuntu
---

### Post by honeybear on 2012-12-05
Hi,

I would like that all users can make blink for whole machine led keyboard system. 

permission error. Any idea to pass this?

thanks

```
setleds -D +scroll < /dev/tty7
-bash: /dev/tty7: Permission denied

```



```

if [ "$2" = "on" ] ; then
  echo "LEDS:Set $1 $2"
  setleds +$1
fi

if [ "$2" = "off" ] ; then
  echo "LEDS:Set $1 $2"
  setleds -$1
fi


if [ "$1 $2" = "blink off" ] ; then
  echo "LEDS:Set $1 $2"
  rm ~/.setled-blink
fi




if [ "$1 $2" = "blink scroll" ] ; then
  echo "LEDS:Set $1 $2"
  touch ~/.setled-blink
  while : ;  do setleds -D -scroll ; sleep 1s; 
   
  if [ ! -f  ~/.setled-blink ] ; then
    echo "** setled blink turned off **"
    exit
  fi
  setleds -D +scroll ; sleep 1s; done
  exit
fi



if [ "$1 $2" = "blink num" ] ; then
  echo "LEDS:Set $1 $2"
  setleds -num
  while : ;  do setleds -D -num ; sleep 1s; setleds -D +num ; sleep 1s; done
fi

```

---

