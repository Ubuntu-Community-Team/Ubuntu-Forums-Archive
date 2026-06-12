---
title: "Text file reconciliation"
date: 2017-05-08
forum: Programming Talk
---

### Post by vennavee on 2017-05-08
i m running the below but getting error
```
######
Log parsing logic
####
#Format the log file
while read line
    do
##Assume $2=sym, $4=buy/sell , $6=qty
    echo $line |awk "{print $2, $4, $6}" >> log_file.txt
    done < log_file.log
# Get log position summary
while read line
    do
    awk -v "line=$line" -F "|"""$1~/line/
    {if $2=="sell"{$3=-1*$3} sum +=$3}
    END {print sum}"" log_file.txt >> log_position.txt
    done < `awk '{print $2} log_file.txt |sort -u


#log_position.txt will have the consolidated positions


############
Get our total positions
##############


#assume sod positions & log positions on same format


    while read line
    do
#Get symbol from line
    symbol=`echo $line |awk -F'' '{print $1}`
#Get SOD positions for the symbol
    sod_pos= `grep $sym sod_positions.txt |awk -F'''{print $2}'
#Get log position for the symbol
    log_pos=`echo $line |awk -F'''{print $2}'`
#Total positions .. need numeric conversion for the below variables
    our_tot_pos = sod_pos + log_pos
#Redirect the output in the format of broker positions files
    echo '$symbol, $log_pos' > our_positions.txt
    done < log_positions.txt
#########
Recon Breaks
#########
    echo "Below are the breaks"
    while read line
    do
    symbol=`echo $line |awk -F '{print $1}'`
    our_pos=`echo $line |awk -F '{print $2}'`
    broker_pos=`grep $symbol broker_position.txt |awk -F '{print $2}'`


    if [[$our_pos -ne $broker_pos]];
    then
    echo "$symbol,$our_pos,$sod_pos"
    fi
    done <our_positions.txt
```

---

### Post by wildmanne39 on 2017-05-08
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by TheFu on 2017-05-08
Which interpreter is being used? sh, bash, ksh?  Did you try the -x switch?
What is the EXACT error, or should we guess?

---

