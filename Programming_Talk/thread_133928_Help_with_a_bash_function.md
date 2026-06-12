---
title: "Help with a bash function"
date: 2006-02-21
forum: Programming Talk
---

### Post by Gandalf on 2006-02-21
Hello,

I am trying to create a function in order to send it a command as a parameter, execute it and display the result in a dialog, it works well if 

```

base_dir="/tmp"
log="/dev/tty5"
dialog=`which dialog`
dorun()
{
	# dorun COMMAND TITLE BEGIN_TEXT END_TEXT
	if [ "${1}" == "" ]; then
		#WTH you need to send the command to run man!!
		return 1
	fi
	FILE=${base_dir}/.dorun
	LOCK=${base_dir}/.dolockrun
	PID=${base_dir}/.dorunpid
	rm -f $FILE > $log 2>&1
	rm -f $LOCK > $log 2>&1
	rm -f $PID > $log 2>&1

	# beginning the loop
	( \
	echo > $FILE; \
	touch $LOCK; \
	if [ "${3}" != "" ]; then
		echo $3 >> $FILE;
	fi
	echo >>$FILE; \
	#$1 >> $FILE; \                                      # The problem is here somewhere in this 3 lines, i can't find it out :(
	i=`echo $1 | sed -e "s:;:; >> \$FILE\n:g"`
	echo -e $i; \
	$i; \
	if [ "${4}" != "" ]; then
		echo $4 >> $FILE;
	fi
	rm -f $LOCK; \
	) &
	sleep 2
	${dialog} --backtitle "$TITLE" --title $2 \
		--no-kill --tailboxbg $FILE 18 70 2>$PID
	while [ -f $LOCK ]; do
		sleep 1
	done
	kill `cat $PID`
	${dialog} --backtitle "$TITLE" --title $2 \
		--exit-label "Continue" --textbox $FILE 18 70
	# fix the stair-stepping that --tailboxbg leaves us with
	stty onlcr

	#rm -f $FILE $LOCK $PID
}

dorun "date ; sleep 10 ; date ; sleep 4" "Test" "begin test" "end test"

```

i tried also
```

( $i ) >> $FILE

```

i don't get what am doing wrong, but i get a weird error everytime i run it, comlaining about date; no such command :-k

---

### Post by Gandalf on 2006-02-21
Never mind, it worked :)

---

### Post by Garyu on 2006-02-21
[QUOTE=Gandalf]Never mind, it worked :)[/QUOTE]

You opened up this thread just to brag about your script, didn't you. ;) *jokingly*

---

