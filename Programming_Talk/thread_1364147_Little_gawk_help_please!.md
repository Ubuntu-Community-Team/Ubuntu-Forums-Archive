---
title: "Little gawk help please!"
date: 2009-12-25
forum: Programming Talk
---

### Post by Barriehie on 2009-12-25
Hey all, Merry Xmas if you do it.  So I've got this list of 'bad' url's that's about 7+ megs and has about 340,000+ lines in it.  Some of the lines have #'s on them to signify comments and most of the lines begin with a preceeding space.  I've got this awk script that so far is stripping out the trailing #.*$ but I'm losing it on removing the preceeding space!  This is for incorporation into my squid blacklist.

Here's a representative sample of the bad list.  I've tried to omit any offensive material.
```

 0-sixty.com
 0.so-0-0-0.phil-peer-rtr1.verizon-gni.net
 0.so-0-2-0.tpa01-bb-rtr1.verizon-gni.net
 0.so-0-2-0.tpa01-bb-rtr2.verizon-gni.net
 0.so-1-2-0.bos-bb-rtr1.verizon-gni.net
 0.so-1-2-0.bos-bb-rtr2.verizon-gni.net
 0.so-3-0-0.ny60-peer-rtr1.verizon-gni.net
 0.so-4-0-0.phil-peer-rtr1.verizon-gni.net
 0.so-5-0-0.xl1.dca5.alter.net
 0.so-5-0-0.xl2.dca5.alter.net                 # Comment
 0.so-5-2-0.lax01-bb-rtr2.verizon-gni.net
 0.so-6-0-0.xt1.lax7.alter.net
 0.so-7-0-0.nwrk-bb-rtr2.verizon-gni.net
 0.so-7-0-0.xl4.nyc4.alter.net                 # Comment
 0.so-7-0-0.xt1.lax7.alter.net
 0.so-7-0-0.xt2.lax7.alter.net
 0-star-0.com
 0-star-0.net
 0-star-0.org
 0.start.bz
 0stats.com
 0st.com
 0stil-100sex.dk
 0t9nry5b5cjw.info
 0texkax7c6hzuidk.com
 0three0.net
 0traff.com
```

Here's the awk script I've got so far.  I've commented out my attempts at removing the preceeding space because it's not working! :(  This is about my 5th attempt at awk scripts, the others work!, but this one is growing grey hairs!  Please help :)
```

#!/usr/bin/gawk
#
# Take my list of bad URL's and strip out the comments following
# the URL and remove the preceeding space at the beginning of
# the line.
#


BEGIN { FS="//n"; IGNORECASE=1 } {

  for ( i=1; i<=NR; i++) {

      #
      # Strip out the comments...
      #
      if ( $i ~ /^.*#.*$/ ) {
          sub(/#.*$/, "", $i)
          $0 == $i
      }

          #
          # Remove the preceeding space at the line beginning
          #
#          if ( $i ~ /^ .*$/ ) {
#              sub(/^ /, "", $i)
#              $0 == $i
#          }

      }

  print $0

}

```

I'm currently letting it run, anything to make the input file smaller!  It's been chugging along for about 1/2 hour so maybe my code isn't efficient or gawk is just slow???

The process is being invoked by:
```

gawk -f badlistfixer.awk allbadhosts.use > ./testfileout

```

The allbadhosts.use file has been sort'ed and uniq'ed so I'm not wasting time with duplicate lines.

TIA,
Barrie

---

### Post by lloyd_b on 2009-12-25
Can't help with the awk/gawk, but here's a sed command that strips the leading spaces, and trims those comments (including the spaces between the URL and the "#"):```
sed -e "s/ *#.*//" -e "s/^ //" inputfile > outputfile
```

Lloyd B.

---

### Post by Barriehie on 2009-12-25
> **lloyd_b said:**
> Can't help with the awk/gawk, but here's a sed command that strips the leading spaces, and trims those comments (including the spaces between the URL and the "#"):```
sed -e "s/ *#.*//" -e "s/^ //" inputfile > outputfile
```

Lloyd B.

Thank you Lloyd!  That worked in the blink of an eye!  I guess I'll have to add yet another 'thing to learn' with ubuntu.  :)

Barrie

---

### Post by ghostdog74 on 2009-12-25
> **Barriehie said:**
>  I guess I'll have to add yet another 'thing to learn' with ubuntu.  :)

just learn to be good with gawk, and there's no need to learn sed AT ALL. 
```

gawk -F'#' '{sub(/^ +/,"",$1);print $1}'  file

```
see my sig for gawk manual, read that from start to finish.

---

### Post by Barriehie on 2009-12-25
> **ghostdog74 said:**
> just learn to be good with gawk, and there's no need to learn sed AT ALL. 
```

gawk -F'#' '{sub(/^ +/,"",$1);print $1}'  file

```
see my sig for gawk manual, read that from start to finish.

Still workin' on it ghostdog74!  I recall your post before when I asked which to pay attention to.  The gawk manual pretty much permanently resides on desktop 2.

Barrie

---

