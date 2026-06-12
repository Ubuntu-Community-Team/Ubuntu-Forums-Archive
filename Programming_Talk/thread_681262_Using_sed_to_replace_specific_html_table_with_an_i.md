---
title: "Using sed to replace specific html table with an image"
date: 2008-01-28
forum: Programming Talk
---

### Post by gopherdoc on 2008-01-28
I've written a script that extracts a table from an html file and converts it into an image.  I need help replacing the original table with the link to the image.  Plucker doesn't like some tables so its a workaround.  All the tables I want to replace start with <table class="prettytable"
Here's what I've done so far (scripting newbie...first real attempt actually)  There are probably better way to do this, but here goes

```

function ps2png {
for i in "$@"
do
        i_new=`dirname $i`/`basename $i .ps`.png
        echo convert $i to $i_new
        gs -dNOPAUSE -sDEVICE=png256 -sOutputFile=$i_new -q -dBATCH $i
#        convert -rotate 90 $i_new $i_new
#        convert -resize 50% $i_new $i_new
done
}
for FL1 in *.html
do
	cat $FL1 | tr -d "\n" >> dump.html
	sgrep '"<table class=\"prettytable\"" .. "</table>"' $FL1 | tr -d "\n" >> ${FL1/html/tmp}
	sed -n '1h;2,$H;${g;s/table>/table>\n/g;p}' ${FL1/html/tmp} > tmp
	NUMOCCR=`sgrep -c '"<table class=\"table\"" .. "</table>"' $FL1`
	COUNTER=0
	if [ "$NUMOCCR" -eq 1 ]; then
		rm ${FL1/.html/}Table0*
		echo "<html><Head></head><body>" >> ${FL1/.html/}Table0.html
		cat tmp >> ${FL1/.html/}Table0.html
		echo "s^" >> tmp.sed;cat tmp >> tmp.sed; echo "^\<img src=\"${FL1/.html/}Table0.png\"/>^" >> tmp.sed
		cat tmp.sed | tr -d "\n" >> temp.sed
		rm tmp.sed
		sed -f temp.sed dump.html > $FL1
		echo "</body></html>">> ${FL1/.html/}Table0.html
		rm ${FL1/html/tmp}
		html2ps -U ${FL1/.html/}Table0.html > ${FL1/.html/}Table0.ps
		ps2png ${FL1/.html/}Table0.ps
		rm ${FL1/.html/}Table0.html
		rm ${FL1/.html/}Table0.ps
		rm temp.sed
	else
		while [ $COUNTER -lt $NUMOCCR ]; do
			rm ${FL1/.html/Table$COUNTER.html}
			echo "<html><Head></head><body>" >> ${FL1/.html/}Table$COUNTER.html 			
			PAGE=`expr $COUNTER + 1`
			cat tmp | sed $PAGE'q;d' >> ${FL1/.html/}Table$COUNTER.html
			echo "s^" >> tmp.sed;cat tmp | sed $PAGE'q;d' >> tmp.sed; echo "^\<img src=\"${FL1/.html/}Table$COUNTER.png\"/>^" >> tmp.sed
			cat tmp.sed | tr -d "\n" >> temp.sed
			rm tmp.sed
   		        sed -f temp.sed dump.html > $FL1
			echo "</body></html>">> ${FL1/.html/}Table$COUNTER.html
			html2ps -U ${FL1/.html/}Table$COUNTER.html > ${FL1/.html/}Table$COUNTER.ps
			ps2png ${FL1/.html/}Table$COUNTER.ps
			rm ${FL1/.html/}Table$COUNTER.html
			rm ${FL1/.html/}Table$COUNTER.ps
			rm temp.sed 
			let COUNTER=COUNTER+1
		done
		rm ${FL1/html/tmp}
	fi
	rm dump.html
done
rm *tmp
gimp -i -b '(batch-autocrop "*.png" 1)' -b '(gimp-quit 0)'

```

This works pretty well for most tables, but fails on others.  I haven't been able to track down the reason why it fails, but I think the sed command runs into a regex character in the table at can't match it to the original.  Any suggestions?

---

### Post by pmasiar on 2008-01-29
It's of course matter of personal preference, but when facing script like yours, I would recommend Python (or even Perl).

Parsing HTML/XML by handcarved regex is a sucker's game. Try some library.

Python's ElementTree is excellent and relatively simple to use (compared with all other XML parsers :-) )

---

### Post by a9bejo on 2008-01-29
> **pmasiar said:**
> 
Python's ElementTree is excellent

Since most websites out there are not written in XHTML, I guess we really don't want a XML Parser here, but a HTML Parser like [hpricot](http://code.whytheluckystiff.net/hpricot/).

---

### Post by gopherdoc on 2008-01-29
then me=sucker :)
The site I'm working with is in XHTML, but i have no experience with python or perl ...time to start learning.  I'll check out ElementTree after a visit to diveintopython.org.  Thanks!

---

