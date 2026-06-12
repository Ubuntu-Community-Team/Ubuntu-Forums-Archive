---
title: "qsub"
date: 2010-03-20
forum: Programming Talk
---

### Post by elad2109 on 2010-03-20
Hey all,

I have a binary file, named "exe1" that receives a parameter. (I don't have its source code).
Executing "exe1" results in creating 3 output files.

I have a bash script that runs "exe1". 
I want to enter "exe1" to cluster queue (using subq command)
But i want to do it more than once, using different parameters each time. 

The problem is that i don't know how to write the scrip so that the output files won't overwrite each other. 

I want to create a new folder for each "exe1" execution. I didn't find any qsub flag that does that. Does somebody knows what the syntax should be?

Thanks

---

### Post by roccivic on 2010-03-20
Make a bash script and use a loop?

[PHP]#!/bin/bash

mkdir test
cd test
list="1 2 3 4 5 6"
for item in $list; do
  mkdir `echo $item`
  cd `echo item`
  echo "foo $item" > somefile.tmp   # substitute this line for your command
  cd ..
done[/PHP]

---

