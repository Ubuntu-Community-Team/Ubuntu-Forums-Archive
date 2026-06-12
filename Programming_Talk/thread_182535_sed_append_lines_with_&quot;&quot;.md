---
title: "sed append lines with &quot;\\&quot;"
date: 2006-05-26
forum: Programming Talk
---

### Post by vladuz976 on 2006-05-26
i am trying to write a shell script that produces latex tables for me, i would like to have every line that i pass to sed end with "\\" i am using the i\ function but no matter what i try i end up with only "\" .Can someone help me"
below is the script with the sed command:


#!/bin/bash
#Eric's script to create latex tables
#this script still needs a lot of work. it will read in the number of columns and rows
#and it will place them depending on the preference of center, left, and right
#read in number of rows and columns
printf "What is the name of your table?\n"
read NAME

read -p "How do you want to lable this table? " LABEL
read -p "What is the caption for this table? " CAPTION
read -p "Name the columns of your table, separated by '&' " COL
read -p "What is the name of the data file? " FILE

printf "How many rows would you like in your table?\n"
read NUM_ROWS

printf "[lrc] stands for 'left', 'right' and 'center' respectively \n"
printf "And how many columns? Please enter as 'ccc' or 'lll'\n"
read NUM_COLUMNS

echo "\begin{table}"
echo "\caption{\label{tab:$LABEL}$CAPTION}"
echo "\begin{ruledtabular}"
echo "\begin{tabular}{$NUM_COLUMNS}"
echo "$COL"
echo "\hline"
sed 's/,/\ \&/g' $FILE | sed 'i\\'
echo "\end{tabular}"
echo "\end{ruledtabular}"
echo "\end{table}"

the table is supposed to look like this:

\begin{table}
\caption{\label{tab:table1}This is a narrow table which fits into a
narrow column}
\begin{ruledtabular}
\begin{tabular}{lcr}
Left & Centered & Right\\
\hline
1 & 2 & 3\\
10 & 20 & 30\\
100 & 200 & 300\\
\end{tabular}
\end{ruledtabular}
\end{table}

---

### Post by hod139 on 2006-05-26
I'm assuming the input file looks like this:
```

1, 2, 3
10, 20, 30
100, 200, 300
```

Then I would use 
```
sed -e 's/,/\ \&/g' -e 's/$/\ \/\//' ${FILE}
```
which uses the wildcard $ to search for end of line, and replaces it with what you want.

---

### Post by vladuz976 on 2006-05-26
[QUOTE=hod139]I'm assuming the input file looks like this:
```

1, 2, 3
10, 20, 30
100, 200, 300
```

Then I would use 
```
sed -e 's/,/\ \&/g' -e 's/$/\ \/\//' ${FILE}
```
which uses the wildcard $ to search for end of line, and replaces it with what you want.[/QUOTE]

that's right, the columns are either comma or tab deliminated

---

