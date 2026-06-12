---
title: "[gnuplot] HTK label for xtics"
date: 2011-05-15
forum: Programming Talk
---

### Post by hiko-seijuro on 2011-05-15
Hello,

I've got an HTK label file which I want to use to generate xticlabel in gnuplot. The HTK label format is this one:

```
<start> <end> <label>
```

I want to generate xtics which coordonnates are (start+end)/2 and the xticslabel is retrieved from the <label> column

Is there a way to do it directly in gnuplot ?

Thanks for your help

---

### Post by hiko-seijuro on 2011-05-15
I've juste found a solution by using awk. 

First the awk script

```

{
	lab[k++]=$3
	val[j++]=((($2-$1)/2+$1)/5000)
}
END\
{
	for (i=0; i<j-1; i++)
	{printf "\42" lab[i] "\42 " int(val[i]) ","}
	printf "\42" lab[j-1] "\42 " int(val[j-1])
}

```

and now the gnuplot part

```

set xtics(`awk -f <awk_filename> <lab_filename>)

```

replace <???> by wanted values

---

