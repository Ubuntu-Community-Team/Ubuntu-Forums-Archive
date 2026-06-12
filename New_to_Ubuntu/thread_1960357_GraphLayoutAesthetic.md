---
title: "Graph::Layout::Aesthetic"
date: 2012-04-17
forum: New to Ubuntu
---

### Post by mashavecher on 2012-04-17
Hi all.
During installation of Graph::Layout::Aesthetic as a part of g-language module I keep getting 
```

gnuplot> set data style linespoints
             ^
         line 0: Unrecognized option.  See 'help set'.

t/05_GnuPlot.t ............ 21/? 
#   Failed test 'No warnings'
#   at t/05_GnuPlot.t line 13.
#          got: '1'
#     expected: '0'
# Unexpected warnings:
# Unexpected returncode from gnuplot: 256 at /home/mashavecher/Documents/Programs/Graph-Layout-Aesthetic-0.12/blib/lib/Graph/Layout/Aesthetic/Monitor/GnuPlot.pm line 118.
# Looks like you failed 1 test of 21.
# Looks like your test exited with 256 just after 21.
t/05_GnuPlot.t ............ Failed 1/21 subtests 
```
after make test.
I've tried googling but no idea how to solve this.
Thanks in advance

---

