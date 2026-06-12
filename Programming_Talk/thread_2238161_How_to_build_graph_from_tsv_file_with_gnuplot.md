---
title: "How to build graph from tsv file with gnuplot?"
date: 2014-08-06
forum: Programming Talk
---

### Post by gray380 on 2014-08-06
Hi,

For instance, we collect data (Vol1, Vol2,..) from some instances (Inst1, Inst2,..) with some time period (f.e. step in 1 sec).
As a result we have the following table:

Inst	Vol1	Vol2	Vol3	Time
1	1	2	3	00:00
2	2	3	1	00:00
3	3	1	2	00:00
1	3	1	2	00:01
2	2	3	1	00:01
3	1	2	3	00:01

How to build multi-branch (branches - InstX) graphs x(time):y(VolX) for each VolX with gnuplot? 

Best regards,
Serhiy.

---

### Post by Vaphell on 2014-08-06
not sure if i understand the problem correctly but i think it would be roughly something like this

```
set xdata time
set timefmt "%M:%S"
set format x "%M:%S"

set pointintervalbox 3
set style line 1 lc rgb 'red'   lt 1 lw 2 pi -1 ps 1.5
set style line 2 lc rgb 'green' lt 1 lw 2 pi -1 ps 1.5
set style line 3 lc rgb 'blue'  lt 1 lw 2 pi -1 ps 1.5


plot "<( awk -v inst=1 '$1==inst' test.data )" using 5:2 title '1-1' with linespoints linestyle 1 pointtype 5,\
     "<( awk -v inst=1 '$1==inst' test.data )" using 5:3 title '1-2' with linespoints linestyle 1 pointtype 7,\
     "<( awk -v inst=1 '$1==inst' test.data )" using 5:4 title '1-3' with linespoints linestyle 1 pointtype 9,\
     "<( awk -v inst=2 '$1==inst' test.data )" using 5:2 title '2-1' with linespoints linestyle 2 pointtype 5,\
     "<( awk -v inst=2 '$1==inst' test.data )" using 5:3 title '2-2' with linespoints linestyle 2 pointtype 7,\
     "<( awk -v inst=2 '$1==inst' test.data )" using 5:4 title '2-3' with linespoints linestyle 2 pointtype 9,\
     "<( awk -v inst=3 '$1==inst' test.data )" using 5:2 title '3-1' with linespoints linestyle 3 pointtype 5,\
     "<( awk -v inst=3 '$1==inst' test.data )" using 5:3 title '3-2' with linespoints linestyle 3 pointtype 7,\
     "<( awk -v inst=3 '$1==inst' test.data )" using 5:4 title '3-3' with linespoints linestyle 3 pointtype 9

```

---

### Post by gray380 on 2014-08-06
Vaphell, thanks.
I'll check your advise and provide a feedback to you.

---

### Post by gray380 on 2014-08-07
Okay, let me clarify my task. I suppose my English in previous message was not good enough :)
We have unknown quantity of Items, each Item has unknown quantity of Parameters and with some time period (we do not know quantity of cycles) some smart script collects the volumes of all parameters for all items and puts them into the table like this:

Item	Param1	Param2	...	ParamY	Time 
1	Z	Z	Z	Z	00:10
2	Z	Z	Z	Z	00:10
...	Z	Z	Z	Z	00:10
X	Z	Z	Z	Z	00:10
1	Z	Z	Z	Z	01:00 <- time has changed for the next Item 1 and so on
2	Z	Z	Z	Z	01:00
...	Z	Z	Z	Z	01:00
X	Z	Z	Z	Z	01:00

and I want to build graphs for all combinations of ParamY:Time with all Items in it.

The solution provided by Vaphell could work but only when we do know all quantities ;)

PS I almost broke my brain with awk. Seems that I should use arrays, but I'm in trouble with arrays :)

---

### Post by Vaphell on 2014-08-07
```

#!/bin/bash

data=$1
gplot=_graph.gnu

rm _*.tmpdata "$gplot" &>/dev/null


### sort item:col data to separate files in 'time value' format (x y)

awk 'NR==1 { for( c=1; c<=NF; c++ ) col[c]=$c; }
      NR>1 { for( c=2; c<=NF-1; c++ )
             {
               f="_"$1"_"col[c]".tmpdata";
               print $NF, $c >> f;
             } 
           }' "$data"


### generate gnuplot file

cat << 'EOF' > "$gplot"
set xdata time
set timefmt "%M:%S"
set format x "%M:%S"

EOF

declare -A linestyle # linestype from assoc array (itemname->value)
linestyle=( [1]=1 [2]=2 [3]=3 [4]=4 ) # etc
declare -A pointtype # pointtype from assoc array (colname->value)
pointtype=( [Vol1]=3 [Vol2]=5 [Vol3]=7 [Vol4]=9 ) #etc

dfiles=( _*.tmpdata )

plotstr=$( printf 'plot '
           for d in "${dfiles[@]}"
           do
             IFS='__.' read _ item col _ <<< "$d"
             lstyle=$item # linestyle=item, not used
             ptype=${col//[a-zA-Z]/}
             ptype=$(( 2*ptype+1 ))  # pointtype by math from extracted number, not used
             printf '"%s" using 1:2 title "%s" with linespoints linestyle %d pointtype %d,\\\n' "$d" "$item-${col//[a-zA-Z]/}" "${linestyle[$item]}" "${pointtype[$col]}"
           done )
           
plotstr=${plotstr%,*}
plotstr=${plotstr//$'\\\n'/$'\\\n     '}

echo "$plotstr" >> "$gplot"

#### run gnuplot
gnuplot -p "$gplot"

```

it sorts data to temp files for all individual graph lines and then creates gnuplot script with all the files accounted for.

---

