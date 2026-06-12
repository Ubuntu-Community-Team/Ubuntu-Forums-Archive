---
title: "tcl and shell script debugging help"
date: 2009-04-20
forum: Programming Talk
---

### Post by psycho5 on 2009-04-20
Directory Paths:

/home/oj/NetSim/ns-allinone-2.1b8a/ns-2.1b8a/CSFQ

files: my_links.tcl, my_sources.tcl
dirs : SharedLink, utils


/home/oj/NetSim/ns-allinone-2.1b8a/ns-2.1b8a/CSFQ/utils

files: (utility files to perform some math)

max_2ndcol
op_col
parse_bwidth

/home/oj/NetSim/ns-allinone-2.1b8a/ns-2.1b8a/CSFQ/SharedLink/

files: SharedLink.tcl 

5 script files:

run-sharedlink1
run-sharedlink2
run-sharedlink3
run-sharedlink4
run-sharedlink5

2 .g files: (graph files)

SharedLink-alltcp.g
SharedLink-tcpudp.g


Trying to get output from run-sharedlink3

Contents of run-sharedlink3 :

```

#!/bin/csh -f 

set ns_dir = "../../"
set res_dir = "./"
set util_dir = "../utils/"

# c1 and c2 are related to pkt size and sim. time, c is related to link rate, pkt size, and sim. time
# link = 10 Mbps, pkt size = 1000 bytes, and simulation time = 10 sec
#set c1   = 1250
#set c    = 12500
# link = 10 Mbps, pkt size = 1000 bytes, and simulation time = 20 sec
#set c1   = 2500
#set c    = 25000
# link = 10 Mbps, pkt size = 1000 bytes, and simulation time = 30 sec
#set c1   = 3750
#set c    = 37500
# link = 10 Mbps, pkt size = 1000 bytes, and simulation time = 40 sec
#set c1   = 5000
#set c    = 50000
# link = 10 Mbps, pkt size = 1000 bytes, and simulation time = 50 sec
#set c1   = 6250
#set c    = 62500
# link = 10 Mbps, pkt size = 1000 bytes, and simulation time = 60 sec
set c1   = 7500
set c    = 75000
# link = 10 Mbps, pkt size = 1000 bytes, and simulation time = 100 sec
#set c1   = 12500
#set c    = 125000

set numFlows = 32
set exp = tcpudp
set out = fairate

#foreach algo (mtrp)
foreach algo (drr csfq red)

if (-e t) then
rm t
endif

echo "${algo}"

# When executing command - ns SharedLink.tcl, the following will be done: Generate one out.tr and one simulation is run from 0 - eg. 60 sec    
${ns_dir}ns SharedLink.tcl -exp ${exp} -algo ${algo} -numFlows ${numFlows} -out ${out} -buf 64000 -thresh 16000

foreach flowId (0 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 20 21 22 23 24 25 26 27 28 29 30 31)
#foreach flowId (0 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 20 21 22 23 24 25 26 27 28 29 30 31 32 33 34 35 36 37 38 39 40 41 42 43 44 45 46 47 48 49 50 51 52 53 54 55 56 57 58 59 60 61 62 63)

@ n = `awk '$1 == "-" && $3 == "0" && $4 == "1" && $8 == '${flowId}'' out.tr | wc -l`

@ n = ${n} * ${numFlows}

echo ${flowId} ${n} >> t

# foreach flowId ends 
end

# Compute normalised throughput
${util_dir}op_col t ${res_dir}SharedLink-${exp}-${algo}.dat 2 2 div ${c}

# foreach algo ends 
end

#awk '$1 == "+" && $5 == "pareto" && $8 == "31" {print $2, "1"}' out.tr > SharedLink-onoff.dat

gnuplot SharedLink-${exp}.g
gnuplot flowrate.g
#gnuplot SharedLink-onoff.g

echo "DONE"

```

Output given: 
drr
Invalid command name "Queue/MTRP"
while executing
"Queue/MTRP set out_ 3"
invoked from within
"if {$out == "qlen"} {
Queue/MTRP set out_ 1
Queue/DRR set out_ 1
Queue/FRED set out_ 1
Queue/RED set out_ 1
}elseif {$out == "avgq"} {
Queu... "
(file "SharedLink.tcl" line 1074)
csfq
Invalid command name "Queue/MTRP"
while executing
"Queue/MTRP set out_ 3"
invoked from within
"if {$out == "qlen"} {
Queue/MTRP set out_ 1
Queue/DRR set out_ 1
Queue/FRED set out_ 1
Queue/RED set out_ 1
}elseif {$out == "avgq"} {
Queu... "
(file "SharedLink.tcl" line 1074)
red
Invalid command name "Queue/MTRP"
while executing
"Queue/MTRP set out_ 3"
invoked from within
"if {$out == "qlen"} {
Queue/MTRP set out_ 1
Queue/DRR set out_ 1
Queue/FRED set out_ 1
Queue/RED set out_ 1
}elseif {$out == "avgq"} {
Queu... "
(file "SharedLink.tcl" line 1074)
Warning: empty y range [0:0], adjusting to [-1:1]
Cannot open load file 'flowrate.g'
line 0: (No such file or directory)

[oj@localhost Sharedlink]$

Can someone help me with this?

---

### Post by psycho5 on 2009-04-20
Contents of SharedLink.tcl 

```

set ns [new Simulator]

#
#
#  ( c[0], c[1], .., c[numFlows - 1] ) n0 --- n1
#
#

#set nf [open out.nam w]
#$ns namtrace-all $nf
set f [open out.tr w]
$ns trace-all $f

set pktSize    1000
set startTime  0.
set finishTime 60.
set delay      1.
set K          100
set kf         100
set rate       10e+06
set tcpType    Reno

source ../my_sources.tcl
source ../my_links.tcl

# build topology
proc build-topology-alltcp { algo numFlows delay K kf bufSize bufThresh pktSize startTime } {
  global ns
  global rate
  global tcpType

  # build link 
  set n0 [$ns node]
  set n1 [$ns node]
  
  if { $algo == "fifo" } {
    build-fifo-link $n0 $n1 $rate $delay $bufSize $pktSize
  } elseif { $algo == "red" } {
    build-red-link $n0 $n1 $rate $delay $bufSize $bufThresh $pktSize
  } elseif { $algo == "fred" } {
    build-fred-link $n0 $n1 $rate $delay $bufSize $bufThresh $pktSize
  } elseif { $algo == "fredl" } {
    build-fredl-link $n0 $n1 $rate $delay $bufSize $bufThresh $pktSize
  } elseif { $algo == "drr" } {
    build-drr-link $n0 $n1 $rate $delay $bufSize $pktSize
  } elseif { $algo == "csfq" } {
    build-csfq-link $n0 $n1 $rate $delay 1 1 $bufSize $bufThresh $pktSize $K
  } elseif { $algo == "mtrp" } {
    build-mtrp-link $n0 $n1 $rate $delay 1 1 $bufSize $pktSize
  } elseif { $algo == "sfq" } {
    build-sfq-link $n0 $n1 $rate $delay $bufSize $pktSize
  } elseif { $algo == "fq" } {
    build-fq-link $n0 $n1 $rate $delay $bufSize $pktSize  
  }                    

  set new 1
  for {set i 0} {$i < $numFlows} {incr i} {
    if { $algo == "drr" } {
      set new [expr $new + 1]
      set n($new) [$ns node]
      build-drr-link $n($new) $n0 20e+06 $delay $bufSize $pktSize
      build-tcp $tcpType $n($new) $n1 $pktSize 0 $i [expr $startTime + $i*0.001]
    } else {
      build-tcp $tcpType $n0 $n1 $pktSize 0 $i [expr $startTime + $i*0.001]
    } 
  }
  
  if { $algo == "csfq" } {
    # init flows: flowid, weight_, k_ (usec)
    for {set i 0} {$i < $numFlows} {incr i} {
      set-csfq-queue $n0 $n1 $i 1 $kf
    }
  }
}


# build topology
proc build-topology-alludp { algo numFlows delay K kf bufSize bufThresh pktSize startTime } {
  global ns
  global rate
  global tcpType

  # build link 
  set n0 [$ns node]
  #set nid [$n0 id]
  #puts "$nid"
  set n1 [$ns node]
  #set nid [$n1 id]
  #puts "$nid"

  if { $algo == "fifo" } {
    build-fifo-link $n0 $n1 $rate $delay $bufSize $pktSize
  } elseif { $algo == "red" } {
    build-red-link $n0 $n1 $rate $delay $bufSize $bufThresh $pktSize
  } elseif { $algo == "fred" } {
    build-fred-link $n0 $n1 $rate $delay $bufSize $bufThresh $pktSize
  } elseif { $algo == "fredl" } {
    build-fredl-link $n0 $n1 $rate $delay $bufSize $bufThresh $pktSize
  } elseif { $algo == "drr" } {
    build-drr-link $n0 $n1 $rate $delay $bufSize $pktSize
  } elseif { $algo == "csfq" } {
    build-csfq-link $n0 $n1 $rate $delay 1 1 $bufSize $bufThresh $pktSize $K
  } elseif { $algo == "mtrp" } {
    build-mtrp-link $n0 $n1 $rate $delay 1 1 $bufSize $pktSize
  } elseif { $algo == "sfq" } {
    build-sfq-link $n0 $n1 $rate $delay $bufSize $pktSize
  } elseif { $algo == "fq" } {
    build-fq-link $n0 $n1 $rate $delay $bufSize $pktSize  
  }        

  set new 1
  set sndRate 0.9e+06

  for {set i 0} {$i < $numFlows} {incr i} {
    set sndRate [expr $sndRate + 0.1e+06] 
    #puts "$i - sndRate = $sndRate"
    # build udp source
    if { $algo == "drr" } {
      set new [expr $new + 1]
      set n($new) [$ns node]
      #set nid [$n($new) id]
      #puts "$nid"
      build-drr-link $n($new) $n0 20e+06 $delay $bufSize $pktSize
      #build-cbr $n($new) $n1 $pktSize [expr $pktSize*8/$sndRate] 1 $i [expr $startTime + $i*0.001]
      # send rate = (i + 1)*fairate
      build-cbr $n($new) $n1 $pktSize [expr $numFlows*$pktSize*8/(($i + 1)*$rate)] 1 $i [expr $startTime + $i*0.001]
    } else {
      #build-cbr $n0 $n1 $pktSize [expr $pktSize*8/$sndRate] 1 $i [expr $startTime + $i*0.001]
      # send rate = (i + 1)*fairate
      build-cbr $n0 $n1 $pktSize [expr $numFlows*$pktSize*8/(($i + 1)*$rate)] 1 $i [expr $startTime + $i*0.001]
    }
  }
 
  if { $algo == "csfq" } {
    # init flows: flowid, weight_, k_ (usec)
    for {set i 0} {$i < $numFlows} {incr i} {
      set-csfq-queue $n0 $n1 $i 1 $kf
    }
  }
} 


# build topology
proc build-topology-allweb { algo numFlows delay K kf bufSize bufThresh pktSize startTime } {
  global ns
  global rate
  global tcpType

  # build link 
  set n0 [$ns node]
  set n1 [$ns node]
 
  if { $algo == "fifo" } {
    build-fifo-link $n0 $n1 $rate $delay $bufSize $pktSize
  } elseif { $algo == "red" } {
    build-red-link $n0 $n1 $rate $delay $bufSize $bufThresh $pktSize
  } elseif { $algo == "fred" } {
    build-fred-link $n0 $n1 $rate $delay $bufSize $bufThresh $pktSize
  } elseif { $algo == "fredl" } {
    build-fredl-link $n0 $n1 $rate $delay $bufSize $bufThresh $pktSize
  } elseif { $algo == "drr" } {
    build-drr-link $n0 $n1 $rate $delay $bufSize $pktSize
  } elseif { $algo == "csfq" } {
    build-csfq-link $n0 $n1 $rate $delay 1 1 $bufSize $bufThresh $pktSize $K
  } elseif { $algo == "mtrp" } {
    build-mtrp-link $n0 $n1 $rate $delay 1 1 $bufSize $pktSize
  } elseif { $algo == "sfq" } {
    build-sfq-link $n0 $n1 $rate $delay $bufSize $pktSize
  } elseif { $algo == "fq" } {
    build-fq-link $n0 $n1 $rate $delay $bufSize $pktSize  
  }                    

  set new 1
  for {set i 0} {$i < $numFlows} {incr i} {
    if { $algo == "drr" } {
      set new [expr $new + 1]
      set n($new) [$ns node]
      build-drr-link $n($new) $n0 20e+06 $delay $bufSize $pktSize
      build-web $n($new) $n1 $pktSize 1.0s 2.0s 1.0Mb 1.6 $i [expr $startTime + $i*0.001]
    } else {
      build-web $n0 $n1 $pktSize 1.0s 2.0s 1.0Mb 1.6 $i [expr $startTime + $i*0.001]
    } 
  }
  
  if { $algo == "csfq" } {
    # init flows: flowid, weight_, k_ (usec)
    for {set i 0} {$i < $numFlows} {incr i} {
      set-csfq-queue $n0 $n1 $i 1 $kf
    }
  }
}


# build topology
proc build-topology-tcpudp { algo numFlows delay K kf bufSize bufThresh pktSize startTime } {
  global ns
  global rate
  global tcpType
  global numUdp
  global numTcp
  global startTime2

  # build link 
  set n0 [$ns node]
  set n1 [$ns node]
  
  if { $algo == "fifo" } {
    build-fifo-link $n0 $n1 $rate $delay $bufSize $pktSize
  } elseif { $algo == "red" } {
    build-red-link $n0 $n1 $rate $delay $bufSize $bufThresh $pktSize
  } elseif { $algo == "fred" } {
    build-fred-link $n0 $n1 $rate $delay $bufSize $bufThresh $pktSize
  } elseif { $algo == "fredl" } {
    build-fredl-link $n0 $n1 $rate $delay $bufSize $bufThresh $pktSize
  } elseif { $algo == "drr" } {
    build-drr-link $n0 $n1 $rate $delay $bufSize $pktSize
  } elseif { $algo == "csfq" } {
    build-csfq-link $n0 $n1 $rate $delay 1 1 $bufSize $bufThresh $pktSize $K
  } elseif { $algo == "mtrp" } {
    build-mtrp-link $n0 $n1 $rate $delay 1 1 $bufSize $pktSize
  } elseif { $algo == "sfq" } {
    build-sfq-link $n0 $n1 $rate $delay $bufSize $pktSize
  } elseif { $algo == "fq" } {
    build-fq-link $n0 $n1 $rate $delay $bufSize $pktSize  
  }                    

  set new 1
  #set sndRate 3.1e+06
  # now--
  # build tcp sources
  #for {set i 0} {$i < 16} {incr i} {}
  for {set i 0} {$i < $numTcp} {incr i} {
    #set sndRate [expr $sndRate + 0.3e+06]
    if { $algo == "drr" } {
      set new [expr $new + 1]
      set n($new) [$ns node]
      build-drr-link $n($new) $n0 20e+06 $delay $bufSize $pktSize
      build-tcp $tcpType $n($new) $n1 $pktSize 0 $i [expr $startTime + $i*0.001]
    } else {
      build-tcp $tcpType $n0 $n1 $pktSize 0 $i [expr $startTime + $i*0.001]
    }
  }

  # build udp sources
  #for {set i 16} {$i < $numFlows} {incr i} {}
  for {set i $numTcp} {$i < $numFlows} {incr i} {
    if { $algo == "drr" } {
      set new [expr $new + 1]
      set n($new) [$ns node]
      build-drr-link $n($new) $n0 20e+06 $delay $bufSize $pktSize
      build-cbr $n($new) $n1 $pktSize [expr $pktSize*8/1e+06] 1 $i [expr $startTime2 + $i*0.001]
    } else {
      build-cbr $n0 $n1 $pktSize [expr $pktSize*8/1e+06] 1 $i [expr $startTime2 + $i*0.001]
    } 
  }
  
  if { $algo == "csfq" } {
    # init flows: flowid, weight_, k_ (usec)
    for {set i 0} {$i < $numFlows} {incr i} {
      set-csfq-queue $n0 $n1 $i 1 $kf
    }
  }
}


# build topology
proc build-topology-webtcp { algo numFlows delay K kf bufSize bufThresh pktSize startTime } {
  global ns
  global rate
  global tcpType

  # build link 
  set n0 [$ns node]
  set n1 [$ns node]
  
  if { $algo == "fifo" } {
    build-fifo-link $n0 $n1 $rate $delay $bufSize $pktSize
  } elseif { $algo == "red" } {
    build-red-link $n0 $n1 $rate $delay $bufSize $bufThresh $pktSize
  } elseif { $algo == "fred" } {
    build-fred-link $n0 $n1 $rate $delay $bufSize $bufThresh $pktSize
  } elseif { $algo == "fredl" } {
    build-fredl-link $n0 $n1 $rate $delay $bufSize $bufThresh $pktSize
  } elseif { $algo == "drr" } {
    build-drr-link $n0 $n1 $rate $delay $bufSize $pktSize
  } elseif { $algo == "csfq" } {
    build-csfq-link $n0 $n1 $rate $delay 1 1 $bufSize $bufThresh $pktSize $K
  } elseif { $algo == "mtrp" } {
    build-mtrp-link $n0 $n1 $rate $delay 1 1 $bufSize $pktSize
  } elseif { $algo == "sfq" } {
    build-sfq-link $n0 $n1 $rate $delay $bufSize $pktSize
  } elseif { $algo == "fq" } {
    build-fq-link $n0 $n1 $rate $delay $bufSize $pktSize  
  }    
                
  # build tcp source
  set new 1
  #set sndRate 3.1e+06
  #for {set i 0} {$i < 16} {incr i} {}
  for {set i 0} {$i < 32} {incr i} {
    #set sndRate [expr $sndRate + 0.3e+06]
    if { $algo == "drr" } {
      set new [expr $new + 1]
      set n($new) [$ns node]
      build-drr-link $n($new) $n0 20e+06 $delay $bufSize $pktSize
      build-tcp $tcpType $n($new) $n1 $pktSize 0 $i [expr $startTime + $i*0.001]
    } else {
      build-tcp $tcpType $n0 $n1 $pktSize 0 $i [expr $startTime + $i*0.001]
    } 
  }

  #for {set i 16} {$i < $numFlows} {incr i} {}
  for {set i 32} {$i < $numFlows} {incr i} {
    # build web source
    if { $algo == "drr" } {
      set new [expr $new + 1]
      set n($new) [$ns node]
      build-drr-link $n($new) $n0 20e+06 $delay $bufSize $pktSize
      build-web $n($new) $n1 $pktSize 1.0s 2.0s 1.0Mb 1.8 $i [expr $startTime + $i*0.001]
    } else {
      build-web $n0 $n1 $pktSize 1.0s 2.0s 1.0Mb 1.8 $i [expr $startTime + $i*0.001]
    } 
  }
  
  if { $algo == "csfq" } {
    # init flows: flowid, weight_, k_ (usec)
    for {set i 0} {$i < $numFlows} {incr i} {
      set-csfq-queue $n0 $n1 $i 1 $kf
    }
  }
} 


# build topology
proc build-topology-webudp { algo numFlows delay K kf bufSize bufThresh pktSize startTime } {
  global ns
  global rate
  global tcpType

  # build link 
  set n0 [$ns node]
  set n1 [$ns node]
  
  if { $algo == "fifo" } {
    build-fifo-link $n0 $n1 $rate $delay $bufSize $pktSize
  } elseif { $algo == "red" } {
    build-red-link $n0 $n1 $rate $delay $bufSize $bufThresh $pktSize
  } elseif { $algo == "fred" } {
    build-fred-link $n0 $n1 $rate $delay $bufSize $bufThresh $pktSize
  } elseif { $algo == "fredl" } {
    build-fredl-link $n0 $n1 $rate $delay $bufSize $bufThresh $pktSize
  } elseif { $algo == "drr" } {
    build-drr-link $n0 $n1 $rate $delay $bufSize $pktSize
  } elseif { $algo == "csfq" } {
    build-csfq-link $n0 $n1 $rate $delay 1 1 $bufSize $bufThresh $pktSize $K
  } elseif { $algo == "mtrp" } {
    build-mtrp-link $n0 $n1 $rate $delay 1 1 $bufSize $pktSize
  } elseif { $algo == "sfq" } {
    build-sfq-link $n0 $n1 $rate $delay $bufSize $pktSize
  } elseif { $algo == "fq" } {
    build-fq-link $n0 $n1 $rate $delay $bufSize $pktSize  
  }                    

  # build udp source
  set new 1
  #set sndRate 3.1e+06
  for {set i 0} {$i < 16} {incr i} {
    #set sndRate [expr $sndRate + 0.3e+06]
    if { $algo == "drr" } {
      set new [expr $new + 1]
      set n($new) [$ns node]
      build-drr-link $n($new) $n0 20e+06 $delay $bufSize $pktSize
      build-cbr $n($new) $n1 $pktSize [expr $pktSize*8/5e+06] 1 $i [expr $startTime + $i*0.001]
    } else {
      build-cbr $n0 $n1 $pktSize [expr $pktSize*8/5e+06] 1 $i [expr $startTime + $i*0.001]
    }
  }

  for {set i 16} {$i < 32} {incr i} {
    #set sndRate [expr $sndRate + 0.3e+06]
    if { $algo == "drr" } {
      set new [expr $new + 1]
      set n($new) [$ns node]
      build-drr-link $n($new) $n0 20e+06 $delay $bufSize $pktSize
      build-cbr $n($new) $n1 $pktSize [expr $pktSize*8/8e+06] 1 $i [expr $startTime + $i*0.001]
    } else {
      build-cbr $n0 $n1 $pktSize [expr $pktSize*8/8e+06] 1 $i [expr $startTime + $i*0.001]
    }
  }

  for {set i 32} {$i < $numFlows} {incr i} {
    # build web source
    if { $algo == "drr" } {
      set new [expr $new + 1]
      set n($new) [$ns node]
      build-drr-link $n($new) $n0 20e+06 $delay $bufSize $pktSize
      build-web $n($new) $n1 $pktSize 1.0s 2.0s 1.0Mb 1.8 $i [expr $startTime + $i*0.001]
    } else {
      build-web $n0 $n1 $pktSize 1.0s 2.0s 1.0Mb 1.8 $i [expr $startTime + $i*0.001]
    } 
  }
  
  if { $algo == "csfq" } {
    # init flows: flowid, weight_, k_ (usec)
    for {set i 0} {$i < $numFlows} {incr i} {
      set-csfq-queue $n0 $n1 $i 1 $kf
    }
  }
}


# build topology
proc build-topology-webtcpudp { algo numFlows delay K kf bufSize bufThresh pktSize startTime } {
  global ns
  global rate
  global tcpType

  # build link 
  set n0 [$ns node]
  set n1 [$ns node]
  
  if { $algo == "fifo" } {
    build-fifo-link $n0 $n1 $rate $delay $bufSize $pktSize
  } elseif { $algo == "red" } {
    build-red-link $n0 $n1 $rate $delay $bufSize $bufThresh $pktSize
  } elseif { $algo == "fred" } {
    build-fred-link $n0 $n1 $rate $delay $bufSize $bufThresh $pktSize
  } elseif { $algo == "fredl" } {
    build-fredl-link $n0 $n1 $rate $delay $bufSize $bufThresh $pktSize
  } elseif { $algo == "drr" } {
    build-drr-link $n0 $n1 $rate $delay $bufSize $pktSize
  } elseif { $algo == "csfq" } {
    build-csfq-link $n0 $n1 $rate $delay 1 1 $bufSize $bufThresh $pktSize $K
  } elseif { $algo == "mtrp" } {
    build-mtrp-link $n0 $n1 $rate $delay 1 1 $bufSize $pktSize
  } elseif { $algo == "sfq" } {
    build-sfq-link $n0 $n1 $rate $delay $bufSize $pktSize
  } elseif { $algo == "fq" } {
    build-fq-link $n0 $n1 $rate $delay $bufSize $pktSize  
  }                    

  # build udp source
  set new 1
  #set sndRate 0e+06
  #for {set i 0} {$i < 12} {incr i} {}
  for {set i 0} {$i < 24} {incr i} {
    #set sndRate [expr $sndRate + 1e+06]
    if { $algo == "drr" } {
      set new [expr $new + 1]
      set n($new) [$ns node]
      build-drr-link $n($new) $n0 20e+06 $delay $bufSize $pktSize
      build-cbr $n($new) $n1 $pktSize [expr $pktSize*8/5e+06] 1 $i [expr $startTime + $i*0.001]
    } else {
      build-cbr $n0 $n1 $pktSize [expr $pktSize*8/5e+06] 1 $i [expr $startTime + $i*0.001]
    }
  }
 
  # build tcp source
  #for {set i 12} {$i < 22} {incr i} {}
  for {set i 24} {$i < 44} {incr i} {
    if { $algo == "drr" } {
      set new [expr $new + 1]
      set n($new) [$ns node]
      build-drr-link $n($new) $n0 20e+06 $delay $bufSize $pktSize
      build-tcp $tcpType $n($new) $n1 $pktSize 0 $i [expr $startTime + $i*0.001]
    } else {
      build-tcp $tcpType $n0 $n1 $pktSize 0 $i [expr $startTime + $i*0.001]
    } 
  }

  # build web source
  #for {set i 22} {$i < $numFlows} {incr i} {}
  for {set i 44} {$i < $numFlows} {incr i} {
    if { $algo == "drr" } {
      set new [expr $new + 1]
      set n($new) [$ns node]
      build-drr-link $n($new) $n0 20e+06 $delay $bufSize $pktSize
      build-web $n($new) $n1 $pktSize 1.0s 2.0s 0.5Mb 1.8 $i [expr $startTime + $i*0.001]
    } else {
      build-web $n0 $n1 $pktSize 1.0s 2.0s 0.5Mb 1.8 $i [expr $startTime + $i*0.001]
    } 
  }
  
  if { $algo == "csfq" } {
    # init flows: flowid, weight_, k_ (usec)
    for {set i 0} {$i < $numFlows} {incr i} {
      set-csfq-queue $n0 $n1 $i 1 $kf
    }
  }
}


# build topology
proc build-topology-fairtcp { algo numFlows delay K kf bufSize bufThresh pktSize startTime } {
  global ns
  global rate
  global tcpType

  # build link 
  set n0 [$ns node]
  set n1 [$ns node]
  
  if { $algo == "fifo" } {
    build-fifo-link $n0 $n1 $rate $delay $bufSize $pktSize
  } elseif { $algo == "red" } {
    build-red-link $n0 $n1 $rate $delay $bufSize $bufThresh $pktSize
  } elseif { $algo == "fred" } {
    build-fred-link $n0 $n1 $rate $delay $bufSize $bufThresh $pktSize
  } elseif { $algo == "fredl" } {
    build-fredl-link $n0 $n1 $rate $delay $bufSize $bufThresh $pktSize
  } elseif { $algo == "drr" } {
    build-drr-link $n0 $n1 $rate $delay $bufSize $pktSize
  } elseif { $algo == "csfq" } {
    build-csfq-link $n0 $n1 $rate $delay 1 1 $bufSize $bufThresh $pktSize $K
  } elseif { $algo == "mtrp" } {
    build-mtrp-link $n0 $n1 $rate $delay 1 1 $bufSize $pktSize
  } elseif { $algo == "sfq" } {
    build-sfq-link $n0 $n1 $rate $delay $bufSize $pktSize
  } elseif { $algo == "fq" } {
    build-fq-link $n0 $n1 $rate $delay $bufSize $pktSize  
  }                    

  set new 1
  for {set i 0} {$i < $numFlows} {incr i} {
    if { $algo == "drr" } {
      set new [expr $new + 1]
      set n($new) [$ns node]
      build-drr-link $n($new) $n0 20e+06 $delay $bufSize $pktSize
      build-tcp $tcpType $n($new) $n1 $pktSize 0 $i [expr $startTime + $i*0.001]
    } else {
      build-tcp $tcpType $n0 $n1 $pktSize 0 $i [expr $startTime + $i*0.001]
    } 
  }
  
  if { $algo == "csfq" } {
    # init flows: flowid, weight_, k_ (usec)
    for {set i 0} {$i < $numFlows} {incr i} {
      set-csfq-queue $n0 $n1 $i 1 $kf
    }
  }
}


# build topology
proc build-topology-oneudp { algo numFlows delay K kf bufSize bufThresh pktSize startTime } {
  global ns
  global rate
  global tcpType

  # build link 
  set n0 [$ns node]
  set n1 [$ns node]
  
  if { $algo == "fifo" } {
    build-fifo-link $n0 $n1 $rate $delay $bufSize $pktSize
  } elseif { $algo == "red" } {
    build-red-link $n0 $n1 $rate $delay $bufSize $bufThresh $pktSize
  } elseif { $algo == "fred" } {
    build-fred-link $n0 $n1 $rate $delay $bufSize $bufThresh $pktSize
  } elseif { $algo == "fredl" } {
    build-fredl-link $n0 $n1 $rate $delay $bufSize $bufThresh $pktSize
  } elseif { $algo == "drr" } {
    build-drr-link $n0 $n1 $rate $delay $bufSize $pktSize
  } elseif { $algo == "csfq" } {
    build-csfq-link $n0 $n1 $rate $delay 1 1 $bufSize $bufThresh $pktSize $K
  } elseif { $algo == "mtrp" } {
    build-mtrp-link $n0 $n1 $rate $delay 1 1 $bufSize $pktSize
  } elseif { $algo == "sfq" } {
    build-sfq-link $n0 $n1 $rate $delay $bufSize $pktSize
  } elseif { $algo == "fq" } {
    build-fq-link $n0 $n1 $rate $delay $bufSize $pktSize  
  }                    

  # build udp source
  if { $algo == "drr" } {
    set new 2
    set n($new) [$ns node]
    build-drr-link $n($new) $n0 20e+06 $delay $bufSize $pktSize
    build-cbr $n($new) $n1 $pktSize [expr $pktSize*8/10e+06] 1 0 $startTime
  } else {
    build-cbr $n0 $n1 $pktSize [expr $pktSize*8/10e+06] 1 0 $startTime
  }

  for {set i 1} {$i < $numFlows} {incr i} {
    # build tcp source
    if { $algo == "drr" } {
      set new [expr $new + 1]
      set n($new) [$ns node]
      build-drr-link $n($new) $n0 20e+06 $delay $bufSize $pktSize
      build-tcp $tcpType $n($new) $n1 $pktSize 0 $i [expr $startTime + $i*0.001]
    } else {
      build-tcp $tcpType $n0 $n1 $pktSize 0 $i [expr $startTime + $i*0.001]
    } 
  }
  
  if { $algo == "csfq" } {
    # init flows: flowid, weight_, k_ (usec)
    for {set i 0} {$i < $numFlows} {incr i} {
      set-csfq-queue $n0 $n1 $i 1 $kf
    }
  }
}


# build topology
proc build-topology-twoudp { algo numFlows delay K kf bufSize bufThresh pktSize startTime } {
  global ns
  global rate
  global tcpType

  # build link 
  set n0 [$ns node]
  set n1 [$ns node]
 
  if { $algo == "fifo" } {
    build-fifo-link $n0 $n1 $rate $delay $bufSize $pktSize
  } elseif { $algo == "red" } {
    build-red-link $n0 $n1 $rate $delay $bufSize $bufThresh $pktSize
  } elseif { $algo == "fred" } {
    build-fred-link $n0 $n1 $rate $delay $bufSize $bufThresh $pktSize
  } elseif { $algo == "fredl" } {
    build-fredl-link $n0 $n1 $rate $delay $bufSize $bufThresh $pktSize
  } elseif { $algo == "drr" } {
    build-drr-link $n0 $n1 $rate $delay $bufSize $pktSize
  } elseif { $algo == "csfq" } {
    build-csfq-link $n0 $n1 $rate $delay 1 1 $bufSize $bufThresh $pktSize $K
  } elseif { $algo == "mtrp" } {
    build-mtrp-link $n0 $n1 $rate $delay 1 1 $bufSize $pktSize
  } elseif { $algo == "sfq" } {
    build-sfq-link $n0 $n1 $rate $delay $bufSize $pktSize
  } elseif { $algo == "fq" } {
    build-fq-link $n0 $n1 $rate $delay $bufSize $pktSize  
  }                    

  # build udp source
  set new 1
  for {set i 0} {$i < 2} {incr i} {
    if { $algo == "drr" } {
      set new [expr $new + 1]
      set n($new) [$ns node]
      build-drr-link $n($new) $n0 20e+06 $delay $bufSize $pktSize
      build-cbr $n($new) $n1 $pktSize [expr $numFlows*$pktSize*8/(($i + 1)*$rate)] 1 $i [expr $startTime + $i*0.001]
    } else {
      build-cbr $n0 $n1 $pktSize [expr $numFlows*$pktSize*8/(($i + 1)*$rate)] 1 $i [expr $startTime + $i*0.001]
    }
  }

  for {set i 2} {$i < $numFlows} {incr i} {
    # build tcp source
    if { $algo == "drr" } {
      set new [expr $new + 1]
      set n($new) [$ns node]
      build-drr-link $n($new) $n0 20e+06 $delay $bufSize $pktSize
      build-tcp $tcpType $n($new) $n1 $pktSize 0 $i [expr $startTime + $i*0.001]
    } else {
      build-tcp $tcpType $n0 $n1 $pktSize 0 $i [expr $startTime + $i*0.001]
    } 
  }
  
  if { $algo == "csfq" } {
    # init flows: flowid, weight_, k_ (usec)
    for {set i 0} {$i < $numFlows} {incr i} {
      set-csfq-queue $n0 $n1 $i 1 $kf
    }
  }
}


# build topology
proc build-topology-triudp { algo numFlows delay K kf bufSize bufThresh pktSize startTime } {
  global ns
  global rate
  global tcpType

  # build link 
  set n0 [$ns node]
  set n1 [$ns node]
  
  if { $algo == "fifo" } {
    build-fifo-link $n0 $n1 $rate $delay $bufSize $pktSize
  } elseif { $algo == "red" } {
    build-red-link $n0 $n1 $rate $delay $bufSize $bufThresh $pktSize
  } elseif { $algo == "fred" } {
    build-fred-link $n0 $n1 $rate $delay $bufSize $bufThresh $pktSize
  } elseif { $algo == "fredl" } {
    build-fredl-link $n0 $n1 $rate $delay $bufSize $bufThresh $pktSize
  } elseif { $algo == "drr" } {
    build-drr-link $n0 $n1 $rate $delay $bufSize $pktSize
  } elseif { $algo == "csfq" } {
    build-csfq-link $n0 $n1 $rate $delay 1 1 $bufSize $bufThresh $pktSize $K
  } elseif { $algo == "mtrp" } {
    build-mtrp-link $n0 $n1 $rate $delay 1 1 $bufSize $pktSize
  } elseif { $algo == "sfq" } {
    build-sfq-link $n0 $n1 $rate $delay $bufSize $pktSize
  } elseif { $algo == "fq" } {
    build-fq-link $n0 $n1 $rate $delay $bufSize $pktSize  
  }                    

  # build udp source
  set new 1
  for {set i 0} {$i < 3} {incr i} {
    if { $algo == "drr" } {
      set new [expr $new + 1]
      set n($new) [$ns node]
      build-drr-link $n($new) $n0 20e+06 $delay $bufSize $pktSize
      build-cbr $n($new) $n1 $pktSize [expr $numFlows*$pktSize*8/(($i + 1)*$rate)] 1 $i [expr $startTime + $i*0.001]
    } else {
      build-cbr $n0 $n1 $pktSize [expr $numFlows*$pktSize*8/(($i + 1)*$rate)] 1 $i [expr $startTime + $i*0.001]
    }
  }

  for {set i 3} {$i < $numFlows} {incr i} {
    # build tcp source
    if { $algo == "drr" } {
      set new [expr $new + 1]
      set n($new) [$ns node]
      build-drr-link $n($new) $n0 20e+06 $delay $bufSize $pktSize
      build-tcp $tcpType $n($new) $n1 $pktSize 0 $i [expr $startTime + $i*0.001]
    } else {
      build-tcp $tcpType $n0 $n1 $pktSize 0 $i [expr $startTime + $i*0.001]
    } 
  }
  
  if { $algo == "csfq" } {
    # init flows: flowid, weight_, k_ (usec)
    for {set i 0} {$i < $numFlows} {incr i} {
      set-csfq-queue $n0 $n1 $i 1 $kf
    }
  }
}


# build topology for onetcpudp as a function of no. of flows
proc build-topology-onetcpudp { algo numFlows delay K kf bufSize bufThresh pktSize startTime } {
  global ns
  global rate
  global tcpType

  # build link 
  set n0 [$ns node]
  set n1 [$ns node]

  if { $algo == "fifo" } {
    build-fifo-link $n0 $n1 $rate $delay $bufSize $pktSize
  } elseif { $algo == "red" } {
    build-red-link $n0 $n1 $rate $delay $bufSize $bufThresh $pktSize
  } elseif { $algo == "fred" } {
    build-fred-link $n0 $n1 $rate $delay $bufSize $bufThresh $pktSize
  } elseif { $algo == "fredl" } {
    build-fredl-link $n0 $n1 $rate $delay $bufSize $bufThresh $pktSize
  } elseif { $algo == "drr" } {
    build-drr-link $n0 $n1 $rate $delay $bufSize $pktSize
  } elseif { $algo == "csfq" } {
    build-csfq-link $n0 $n1 $rate $delay 1 1 $bufSize $bufThresh $pktSize $K
  } elseif { $algo == "mtrp" } {
    build-mtrp-link $n0 $n1 $rate $delay 1 1 $bufSize $pktSize
  } elseif { $algo == "sfq" } {
    build-sfq-link $n0 $n1 $rate $delay $bufSize $pktSize
  } elseif { $algo == "fq" } {
    build-fq-link $n0 $n1 $rate $delay $bufSize $pktSize  
  }        

  # build tcp 
  if { $algo == "drr" } {
    set new 2
    set n($new) [$ns node]
    build-drr-link $n($new) $n0 20e+06 $delay $bufSize $pktSize
    build-tcp $tcpType $n($new) $n1 $pktSize 0 0 $startTime
  } else {
    build-tcp $tcpType $n0 $n1 $pktSize 0 0 $startTime
  }

  # build background traffic of udp
  for {set i 1} {$i < $numFlows} {incr i} {
    if { $algo == "drr" } {
      set new [expr $new + 1]
      set n($new) [$ns node]
      build-drr-link $n($new) $n0 20e+06 $delay $bufSize $pktSize
      # set cbr rate to n*fairshare using ($numFlows*$pktSize*8)/(n*$rate)
      build-cbr $n($new) $n1 $pktSize [expr ($numFlows*$pktSize*8)/(1*$rate)] 1 $i [expr $startTime + $i*0.001]
      #build-cbr $n($new) $n1 $pktSize [expr $pktSize*8/0.5e+06] 1 $i [expr $startTime + $i*0.001]
    } else {
      # set cbr rate to n*fairshare using ($numFlows*$pktSize*8)/(n*$rate)
      build-cbr $n0 $n1 $pktSize [expr ($numFlows*$pktSize*8)/(1*$rate)] 1 $i [expr $startTime + $i*0.001]
      #build-cbr $n0 $n1 $pktSize [expr $pktSize*8/0.5e+06] 1 $i [expr $startTime + $i*0.001]
    }
  }

  if { $algo == "csfq" } {
    # init flows: flowid, weight_, k_ (usec)
    for {set i 0} {$i < $numFlows} {incr i} {
      set-csfq-queue $n0 $n1 $i 1 $kf
    }
  }
}


# build topology for onetcpweb as a function of no. of flows
proc build-topology-onetcpweb { algo numFlows delay K kf bufSize bufThresh pktSize startTime } {
  global ns
  global rate
  global tcpType

  # build link 
  set n0 [$ns node]
  set n1 [$ns node]

  if { $algo == "fifo" } {
    build-fifo-link $n0 $n1 $rate $delay $bufSize $pktSize
  } elseif { $algo == "red" } {
    build-red-link $n0 $n1 $rate $delay $bufSize $bufThresh $pktSize
  } elseif { $algo == "fred" } {
    build-fred-link $n0 $n1 $rate $delay $bufSize $bufThresh $pktSize
  } elseif { $algo == "fredl" } {
    build-fredl-link $n0 $n1 $rate $delay $bufSize $bufThresh $pktSize
  } elseif { $algo == "drr" } {
    build-drr-link $n0 $n1 $rate $delay $bufSize $pktSize
  } elseif { $algo == "csfq" } {
    build-csfq-link $n0 $n1 $rate $delay 1 1 $bufSize $bufThresh $pktSize $K
  } elseif { $algo == "mtrp" } {
    build-mtrp-link $n0 $n1 $rate $delay 1 1 $bufSize $pktSize
  } elseif { $algo == "sfq" } {
    build-sfq-link $n0 $n1 $rate $delay $bufSize $pktSize
  } elseif { $algo == "fq" } {
    build-fq-link $n0 $n1 $rate $delay $bufSize $pktSize  
  }        

  # build tcp 
  if { $algo == "drr" } {
    set new 2
    set n($new) [$ns node]
    build-drr-link $n($new) $n0 20e+06 $delay $bufSize $pktSize
    build-tcp $tcpType $n($new) $n1 $pktSize 0 0 $startTime
  } else {
    build-tcp $tcpType $n0 $n1 $pktSize 0 0 $startTime
  }

  # build background traffic of web
  for {set i 1} {$i < $numFlows} {incr i} {
    if { $algo == "drr" } {
      set new [expr $new + 1]
      set n($new) [$ns node]
      build-drr-link $n($new) $n0 20e+06 $delay $bufSize $pktSize
      #build-web $n($new) $n1 $pktSize 1.0s 2.0s [expr 1*$rate/$numFlows]b 1.6 $i [expr $startTime + $i*0.001]
      build-web $n($new) $n1 $pktSize 1.0s 2.0s 2.0Mb 1.8 $i [expr $startTime + $i*0.001]
    } else {
      #build-web $n0 $n1 $pktSize 1.0s 2.0s [expr 1*$rate/$numFlows]b 1.6 $i [expr $startTime + $i*0.001]
      build-web $n0 $n1 $pktSize 1.0s 2.0s 2.0Mb 1.8 $i [expr $startTime + $i*0.001]
    }
  }

  if { $algo == "csfq" } {
    # init flows: flowid, weight_, k_ (usec)
    for {set i 0} {$i < $numFlows} {incr i} {
      set-csfq-queue $n0 $n1 $i 1 $kf
    }
  }
}


# build topology for oneudptcp as a function of no. of flows
proc build-topology-oneudptcp { algo numFlows delay K kf bufSize bufThresh pktSize startTime } {
  global ns
  global rate
  global tcpType

  # build link 
  set n0 [$ns node]
  set n1 [$ns node]

  if { $algo == "fifo" } {
    build-fifo-link $n0 $n1 $rate $delay $bufSize $pktSize
  } elseif { $algo == "red" } {
    build-red-link $n0 $n1 $rate $delay $bufSize $bufThresh $pktSize
  } elseif { $algo == "fred" } {
    build-fred-link $n0 $n1 $rate $delay $bufSize $bufThresh $pktSize
  } elseif { $algo == "fredl" } {
    build-fredl-link $n0 $n1 $rate $delay $bufSize $bufThresh $pktSize
  } elseif { $algo == "drr" } {
    build-drr-link $n0 $n1 $rate $delay $bufSize $pktSize
  } elseif { $algo == "csfq" } {
    build-csfq-link $n0 $n1 $rate $delay 1 1 $bufSize $bufThresh $pktSize $K
  } elseif { $algo == "mtrp" } {
    build-mtrp-link $n0 $n1 $rate $delay 1 1 $bufSize $pktSize
  } elseif { $algo == "sfq" } {
    build-sfq-link $n0 $n1 $rate $delay $bufSize $pktSize
  } elseif { $algo == "fq" } {
    build-fq-link $n0 $n1 $rate $delay $bufSize $pktSize  
  }        

  # build tcp or udp 
  if { $algo == "drr" } {
    set new 2
    set n($new) [$ns node]
    build-drr-link $n($new) $n0 20e+06 $delay $bufSize $pktSize
    build-tcp $tcpType $n($new) $n1 $pktSize 0 0 $startTime
    #build-cbr $n($new) $n1 $pktSize [expr $pktSize*8/5e+06] 1 0 $startTime
    #build-cbr $n($new) $n1 $pktSize [expr ($numFlows*$pktSize*8)/(2*$rate)] 1 0 $startTime
  } else {
    build-tcp $tcpType $n0 $n1 $pktSize 0 0 $startTime
    #build-cbr $n0 $n1 $pktSize [expr $pktSize*8/5e+06] 1 0 $startTime
    #build-cbr $n0 $n1 $pktSize [expr ($numFlows*$pktSize*8)/(2*$rate)] 1 0 $startTime
  }

  # build background traffic of tcp, udp or web
  for {set i 1} {$i < $numFlows} {incr i} {
    if { $algo == "drr" } {
      set new [expr $new + 1]
      set n($new) [$ns node]
      build-drr-link $n($new) $n0 20e+06 $delay $bufSize $pktSize
      build-cbr $n($new) $n1 $pktSize [expr ($numFlows*$pktSize*8)/(1*$rate)] 1 $i [expr $startTime + $i*0.001]
      #build-cbr $n($new) $n1 $pktSize [expr $pktSize*8/0.5e+06] 1 $i [expr $startTime + $i*0.001]
      #build-web $n($new) $n1 $pktSize 1.0s 2.0s [expr 1*$rate/$numFlows]b 1.6 $i [expr $startTime + $i*0.001]
      #build-web $n($new) $n1 $pktSize 1.0s 2.0s 3.0Mb 1.8 $i [expr $startTime + $i*0.001]
      #build-tcp $tcpType $n($new) $n1 $pktSize 0 $i [expr $startTime + $i*0.001]
    } else {
      build-cbr $n0 $n1 $pktSize [expr ($numFlows*$pktSize*8)/(2*$rate)] 1 $i [expr $startTime + $i*0.001]
      #build-cbr $n0 $n1 $pktSize [expr $pktSize*8/0.5e+06] 1 $i [expr $startTime + $i*0.001]
      #build-web $n0 $n1 $pktSize 1.0s 2.0s [expr 1*$rate/$numFlows]b 1.6 $i [expr $startTime + $i*0.001]
      build-web $n0 $n1 $pktSize 1.0s 2.0s 3.0Mb 1.8 $i [expr $startTime + $i*0.001]
      #build-tcp $tcpType $n0 $n1 $pktSize 0 $i [expr $startTime + $i*0.001]
    }
  }

  if { $algo == "csfq" } {
    # init flows: flowid, weight_, k_ (usec)
    for {set i 0} {$i < $numFlows} {incr i} {
      set-csfq-queue $n0 $n1 $i 1 $kf
    }
  }
}


# build topology for oneudpweb as a function of no. of flows
proc build-topology-oneudpweb { algo numFlows delay K kf bufSize bufThresh pktSize startTime } {
  global ns
  global rate
  global tcpType

  # build link 
  set n0 [$ns node]
  set n1 [$ns node]

  if { $algo == "fifo" } {
    build-fifo-link $n0 $n1 $rate $delay $bufSize $pktSize
  } elseif { $algo == "red" } {
    build-red-link $n0 $n1 $rate $delay $bufSize $bufThresh $pktSize
  } elseif { $algo == "fred" } {
    build-fred-link $n0 $n1 $rate $delay $bufSize $bufThresh $pktSize
  } elseif { $algo == "fredl" } {
    build-fredl-link $n0 $n1 $rate $delay $bufSize $bufThresh $pktSize
  } elseif { $algo == "drr" } {
    build-drr-link $n0 $n1 $rate $delay $bufSize $pktSize
  } elseif { $algo == "csfq" } {
    build-csfq-link $n0 $n1 $rate $delay 1 1 $bufSize $bufThresh $pktSize $K
  } elseif { $algo == "mtrp" } {
    build-mtrp-link $n0 $n1 $rate $delay 1 1 $bufSize $pktSize
  } elseif { $algo == "sfq" } {
    build-sfq-link $n0 $n1 $rate $delay $bufSize $pktSize
  } elseif { $algo == "fq" } {
    build-fq-link $n0 $n1 $rate $delay $bufSize $pktSize  
  }        

  # build tcp or udp 
  if { $algo == "drr" } {
    set new 2
    set n($new) [$ns node]
    build-drr-link $n($new) $n0 20e+06 $delay $bufSize $pktSize
    build-tcp $tcpType $n($new) $n1 $pktSize 0 0 $startTime
    #build-cbr $n($new) $n1 $pktSize [expr $pktSize*8/5e+06] 1 0 $startTime
    #build-cbr $n($new) $n1 $pktSize [expr ($numFlows*$pktSize*8)/(2*$rate)] 1 0 $startTime
  } else {
    build-tcp $tcpType $n0 $n1 $pktSize 0 0 $startTime
    #build-cbr $n0 $n1 $pktSize [expr $pktSize*8/5e+06] 1 0 $startTime
    #build-cbr $n0 $n1 $pktSize [expr ($numFlows*$pktSize*8)/(2*$rate)] 1 0 $startTime
  }

  # build background traffic of tcp, udp or web
  for {set i 1} {$i < $numFlows} {incr i} {
    if { $algo == "drr" } {
      set new [expr $new + 1]
      set n($new) [$ns node]
      build-drr-link $n($new) $n0 20e+06 $delay $bufSize $pktSize
      build-cbr $n($new) $n1 $pktSize [expr ($numFlows*$pktSize*8)/(1*$rate)] 1 $i [expr $startTime + $i*0.001]
      #build-cbr $n($new) $n1 $pktSize [expr $pktSize*8/0.5e+06] 1 $i [expr $startTime + $i*0.001]
      #build-web $n($new) $n1 $pktSize 1.0s 2.0s [expr 1*$rate/$numFlows]b 1.6 $i [expr $startTime + $i*0.001]
      #build-web $n($new) $n1 $pktSize 1.0s 2.0s 3.0Mb 1.8 $i [expr $startTime + $i*0.001]
      #build-tcp $tcpType $n($new) $n1 $pktSize 0 $i [expr $startTime + $i*0.001]
    } else {
      build-cbr $n0 $n1 $pktSize [expr ($numFlows*$pktSize*8)/(2*$rate)] 1 $i [expr $startTime + $i*0.001]
      #build-cbr $n0 $n1 $pktSize [expr $pktSize*8/0.5e+06] 1 $i [expr $startTime + $i*0.001]
      #build-web $n0 $n1 $pktSize 1.0s 2.0s [expr 1*$rate/$numFlows]b 1.6 $i [expr $startTime + $i*0.001]
      build-web $n0 $n1 $pktSize 1.0s 2.0s 3.0Mb 1.8 $i [expr $startTime + $i*0.001]
      #build-tcp $tcpType $n0 $n1 $pktSize 0 $i [expr $startTime + $i*0.001]
    }
  }

  if { $algo == "csfq" } {
    # init flows: flowid, weight_, k_ (usec)
    for {set i 0} {$i < $numFlows} {incr i} {
      set-csfq-queue $n0 $n1 $i 1 $kf
    }
  }
}


# build topology
proc build-topology { exp algo numFlows delay K kf bufSize bufThresh pktSize startTime } {
  if { $exp == "alltcp" } {
    build-topology-alltcp $algo $numFlows $delay $K $kf $bufSize $bufThresh $pktSize $startTime
  } elseif { $exp == "alludp" } {
    build-topology-alludp $algo $numFlows $delay $K $kf $bufSize $bufThresh $pktSize $startTime
  } elseif { $exp == "allweb" } {
    build-topology-allweb $algo $numFlows $delay $K $kf $bufSize $bufThresh $pktSize $startTime
  } elseif { $exp == "tcpudp" } {
    build-topology-tcpudp $algo $numFlows $delay $K $kf $bufSize $bufThresh $pktSize $startTime
  } elseif { $exp == "webtcp" } {
    build-topology-webtcp $algo $numFlows $delay $K $kf $bufSize $bufThresh $pktSize $startTime
  } elseif { $exp == "webudp" } {
    build-topology-webudp $algo $numFlows $delay $K $kf $bufSize $bufThresh $pktSize $startTime
  } elseif { $exp == "webtcpudp" } {
    build-topology-webtcpudp $algo $numFlows $delay $K $kf $bufSize $bufThresh $pktSize $startTime
  } elseif { $exp == "fairtcp" } {
    build-topology-alltcp $algo $numFlows $delay $K $kf $bufSize $bufThresh $pktSize $startTime
  } elseif { $exp == "oneudp" } {
    build-topology-oneudp $algo $numFlows $delay $K $kf $bufSize $bufThresh $pktSize $startTime
  } elseif { $exp == "twoudp" } {
    build-topology-twoudp $algo $numFlows $delay $K $kf $bufSize $bufThresh $pktSize $startTime
  } elseif { $exp == "triudp" } {
    build-topology-triudp $algo $numFlows $delay $K $kf $bufSize $bufThresh $pktSize $startTime
  } elseif { $exp == "onetcpudp" } {
    build-topology-onetcpudp $algo $numFlows $delay $K $kf $bufSize $bufThresh $pktSize $startTime
  } elseif { $exp == "onetcpweb" } {
    build-topology-onetcpweb $algo $numFlows $delay $K $kf $bufSize $bufThresh $pktSize $startTime
  } elseif { $exp == "oneudptcp" } {
    build-topology-oneudptcp $algo $numFlows $delay $K $kf $bufSize $bufThresh $pktSize $startTime
  } elseif { $exp == "oneudpweb" } {
    build-topology-oneudpweb $algo $numFlows $delay $K $kf $bufSize $bufThresh $pktSize $startTime
  }
}


# Read command line arguments
for {set i 0} {$i < $argc} {incr i} {
  set opt1 [lindex $argv $i]
  if {$opt1 == "-algo"} {
    set algo [lindex $argv [incr i]]
  } elseif {$opt1 == "-exp"} {
    set exp [lindex $argv [incr i]]
  } elseif {$opt1 == "-numFlows"} { 
    set numFlows [lindex $argv [incr i]]
  } elseif {$opt1 == "-K"} {
    set K [lindex $argv [incr i]]
  } elseif {$opt1 == "-kf"} {
    set kf [lindex $argv [incr i]]
  } elseif {$opt1 == "-buf"} {
    set bufSize [lindex $argv [incr i]]
  } elseif {$opt1 == "-thresh"} {
    set bufThresh [lindex $argv [incr i]]
  } elseif {$opt1 == "-delay"} {
    set delay [lindex $argv [incr i]]
  } elseif {$opt1 == "-out"} {
    set out [lindex $argv [incr i]]
  }
}

set startTime2 0.0 
set updateInt 500.0 
set numUdp 16  
set numTcp [expr $numFlows - $numUdp]

# The binding statements (eg. Queue/MTRP set out_ 1) must be executed before build-link statements (eg. build-mtrp-link $n0 $n1......). The build-link statements include the installations of algorithms at nodes (eg. MTRP is installed at n0 & n1) 

if {$out == "qlen"} {
  Queue/MTRP set out_ 1
  Queue/DRR set out_ 1
  Queue/FRED set out_ 1
  Queue/RED set out_ 1
} elseif {$out == "avgq"} {
  Queue/MTRP set out_ 2
  Queue/DRR set out_ 2
  Queue/FRED set out_ 2
  Queue/RED set out_ 2
} elseif {$out == "fairate"} {
  Queue/MTRP set out_ 3
  Queue/DRR set out_ 3
  Queue/FRED set out_ 3
  Queue/RED set out_ 3
} else {
  Queue/MTRP set out_ 0
  Queue/DRR set out_ 0
  Queue/FRED set out_ 0
  Queue/RED set out_ 0
}

Queue/MTRP set edge_ 1
Queue/MTRP set rate_ 10.0
Queue/MTRP set qlim_ 512000
Queue/FRED set many-flows_ 0

Queue/MTRP set numFlows_ $numFlows
Queue/MTRP set numUdp $numUdp
Queue/MTRP set numTcp $numTcp
Queue/MTRP set simTime_ $finishTime
Queue/MTRP set updateInt $updateInt
Queue/DRR set numFlows_ $numFlows
Queue/DRR set simTime_ $finishTime
Queue/FRED set numFlows_ $numFlows
Queue/FRED set simTime_ $finishTime
Queue/RED set numFlows_ $numFlows
Queue/RED set simTime_ $finishTime

build-topology $exp $algo $numFlows $delay $K $kf $bufSize $bufThresh $pktSize $startTime

$ns at $finishTime "finish"  

proc finish {} {
  global ns nf f
  $ns flush-trace
  #close $nf
  close $f
  #exec nam out.nam &
  exit 0
}

$ns run

```

---

### Post by claird on 2009-04-20
> **psycho5 said:**
> Directory Paths:

/home/oj/NetSim/ns-allinone-2.1b8a/ns-2.1b8a/CSFQ
... [hundreds of lines later] ...

Output given: 
drr
Invalid command name "Queue/MTRP"
while executing
"Queue/MTRP set out_ 3"
invoked from within
"if {$out == "qlen"} {
Queue/MTRP set out_ 1
Queue/DRR set out_ 1
Queue/FRED set out_ 1
Queue/RED set out_ 1
}elseif {$out == "avgq"} {
Queu... "
(file "SharedLink.tcl" line 1074)
csfq
Invalid command name "Queue/MTRP"
while executing
"Queue/MTRP set out_ 3"
invoked from within
"if {$out == "qlen"} {
Queue/MTRP set out_ 1
Queue/DRR set out_ 1
Queue/FRED set out_ 1
Queue/RED set out_ 1
}elseif {$out == "avgq"} {
Queu... "
(file "SharedLink.tcl" line 1074)
red
Invalid command name "Queue/MTRP"
while executing
"Queue/MTRP set out_ 3"
invoked from within
"if {$out == "qlen"} {
Queue/MTRP set out_ 1
Queue/DRR set out_ 1
Queue/FRED set out_ 1
Queue/RED set out_ 1
}elseif {$out == "avgq"} {
Queu... "
(file "SharedLink.tcl" line 1074)
Warning: empty y range [0:0], adjusting to [-1:1]
Cannot open load file 'flowrate.g'
line 0: (No such file or directory)

[oj@localhost Sharedlink]$

Can someone help me with this?

You've got a lot going on here--more than any one reply can address.

There's nothing essential in your shell scripting here, by the way; as you present it, this is purely a Tcl issue.

Briefly, the issue is exactly what the Tcl interpreter reports:  your script SharedLink.tcl tries to use a command named "Queue/MTRP", but no one has defined such a command.

Several questions arise:  are you a Tcl programmer yourself?  Are you using a standard Tcl interpreter, or perhaps one that has been modified to build in such special simulation commands as "Queue/MTRP"?  Are "mysources.tcl" supposed to define "Queue/MTRP"?

---

