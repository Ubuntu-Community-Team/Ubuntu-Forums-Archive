---
title: "qsub - beowulf cluster outupt file"
date: 2009-12-07
forum: Programming Talk
---

### Post by abraxas334 on 2009-12-07
Hi,
I am submitting jobs to a cluster using qsub. I am using a submission script, which is the "demo" script of my cluster. It creates a series of outputfiles in the directory i am submitting the jobs, I would like them to be put into an output directory. Is that possible? And if so how. Here is my submission script i am using:

[PHP]

#!/bin/bash


# This is an example submit script for the hello world program.

# OPTIONS FOR GRID ENGINE ==============================================================
#
# Options for Grid Engine can be put in your submission command line like ordinary flags.
# like the "-cwd" option in this example: 
# "qsub -cwd hello_world.sh"
#
# Alternatively you can place them in you submit script thus:

#$ -cwd
# This send output into the directory from which you submitted

#$ -j y
# Join up output and error into one file

#$ -t 1-40
# This is the task request for 10 task labelled 1 to 10

# OPTIONS FOR GRID ENGINE=================================================================



# Here we just use Unix command to run our program

echo "Running on `hostname`"
./TPS_run commandlinearguments $SGE_TASK_ID

# This script just gives the value of the SGE_TASK_ID variable


echo  "The TASK ID of *this* task is : $SGE_TASK_ID"

#echo "If I named my input file INPUT.$SGE_TASK_ID, I could do clever things"


echo "Finished job now"



[/PHP]

---

