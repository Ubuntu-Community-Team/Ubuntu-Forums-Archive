---
title: "please show how to put these 2 scrolling HTML text windows side by side?"
date: 2011-01-23
forum: Programming Talk
---

### Post by sdowney717 on 2011-01-23
I pulled these off the forums
save it as an htm file and run in the browser

```

<!--shows a working scrolling text window -->

<br />

<div style="margin:700px; margin-top:5px">
	<div class="smallfont" style="margin-bottom:2px">Code:</div>

	<pre class="alt2" dir="ltr" style="
		margin: 0px;
		padding: 6px;
		border: 1px inset;
		width: 640px;
		height: 500px;
		text-align: left;
		overflow: auto">#!/bin/bash 

#######################
# Author:phoenix122
# Version:1.0
#######################

# Turn on extended pattern matching for vm_starter function to work 
shopt -s extglob 

trap error_exit SIGHUP SIGINT SIGTERM

#############################################################
#############################################################

# Housekeeping, error handling, ease of use

function clean_up 
{
	# Perform Housekeeping
	# Accepts an exit status
	rm -f $TEMP_FILE ; rm -f $TEMP_FILE2
	exit $1
}


c

selection= 
vrde=&quot;--vrde off&quot; 

#### Constants
TEMP_FILE=$TEMP_DIR/vmh.$$.$RANDOM
TEMP_FILE2=$TEMP_DIR/vbhcom.$RANDOM.$$
PROGNAME=$(basename $0)

until [ &quot;$selection&quot; = &quot;0&quot; ]; do
    echo &quot;Virtual Machine Menu&quot;
	echo &quot;&quot;
    echo &quot;1 - Start a Virtual Machine with default options&quot;

    echo &quot;2 - Change default options&quot;
	echo &quot;3 - View current Virtual Machines&quot;
	echo &quot;&quot;
    echo &quot;0 - Exit&quot;
	echo &quot;&quot;

    echo -n &quot;Enter selection: &quot;
    read selection
    echo &quot;&quot;
    case $selection in
        1 ) clear ; vm_starter ;;
        2 ) default_options ; press_enter ;;
		3 ) list_vm ; press_enter ;;
		0 ) clear ; clean_up ; exit ;;
		* ) echo &quot;Please enter 1, 2, or 0&quot;
    esac
done

</pre>
</div></div>
		<!-- / message -->
		
<div style="margin:10px; margin-top:5px">
	<div class="smallfont" style="margin-bottom:2px">Code:</div>

	<pre class="alt2" dir="ltr" style="
		margin: 0px;
		padding: 6px;
		border: 1px inset;
		width: 640px;
		height: 500px;
		text-align: left;
		overflow: auto">#!/bin/bash 

#######################
# Author:phoenix122
# Version:1.0
#######################

# Turn on extended pattern matching for vm_starter function to work 
shopt -s extglob 

trap error_exit SIGHUP SIGINT SIGTERM

#############################################################
#############################################################

# Housekeeping, error handling, ease of use

function clean_up 
{
	# Perform Housekeeping
	# Accepts an exit status
	rm -f $TEMP_FILE ; rm -f $TEMP_FILE2
	exit $1
}


c

selection= 
vrde=&quot;--vrde off&quot; 

#### Constants
TEMP_FILE=$TEMP_DIR/vmh.$$.$RANDOM
TEMP_FILE2=$TEMP_DIR/vbhcom.$RANDOM.$$
PROGNAME=$(basename $0)

until [ &quot;$selection&quot; = &quot;0&quot; ]; do
    echo &quot;Virtual Machine Menu&quot;
	echo &quot;&quot;
    echo &quot;1 - Start a Virtual Machine with default options&quot;

    echo &quot;2 - Change default options&quot;
	echo &quot;3 - View current Virtual Machines&quot;
	echo &quot;&quot;
    echo &quot;0 - Exit&quot;
	echo &quot;&quot;

    echo -n &quot;Enter selection: &quot;
    read selection
    echo &quot;&quot;
    case $selection in
        1 ) clear ; vm_starter ;;
        2 ) default_options ; press_enter ;;
		3 ) list_vm ; press_enter ;;
		0 ) clear ; clean_up ; exit ;;
		* ) echo &quot;Please enter 1, 2, or 0&quot;
    esac
done

</pre>
</div></div>
		<!-- / message -->		



```

---

### Post by sdowney717 on 2011-01-23
ok, it is solved by using the float property.
and setting the width on one of the boxes much bigger

```

<!--shows a working scrolling text window -->

<br />

<div style="float: left; margin:10px; width: 720px; margin-right: 5px;">
<!--<div style="margin:10px; margin-top:5px ">-->
	<div class="smallfont" style="margin-bottom:2px">Code:</div>

	<pre class="alt2" dir="ltr" style="
		margin: 0px;
		padding: 6px;
		border: 1px inset;
		width: 640px;
		height: 500px;
		text-align: left;
		overflow: auto">#!/bin/bash 

#######################
# Author:phoenix122
# Version:1.0
#######################

# Turn on extended pattern matching for vm_starter function to work 
shopt -s extglob 

trap error_exit SIGHUP SIGINT SIGTERM

#############################################################
#############################################################

# Housekeeping, error handling, ease of use

function clean_up 
{
	# Perform Housekeeping
	# Accepts an exit status
	rm -f $TEMP_FILE ; rm -f $TEMP_FILE2
	exit $1
}


c

selection= 
vrde=&quot;--vrde off&quot; 

#### Constants
TEMP_FILE=$TEMP_DIR/vmh.$$.$RANDOM
TEMP_FILE2=$TEMP_DIR/vbhcom.$RANDOM.$$
PROGNAME=$(basename $0)

until [ &quot;$selection&quot; = &quot;0&quot; ]; do
    echo &quot;Virtual Machine Menu&quot;
	echo &quot;&quot;
    echo &quot;1 - Start a Virtual Machine with default options&quot;

    echo &quot;2 - Change default options&quot;
	echo &quot;3 - View current Virtual Machines&quot;
	echo &quot;&quot;
    echo &quot;0 - Exit&quot;
	echo &quot;&quot;

    echo -n &quot;Enter selection: &quot;
    read selection
    echo &quot;&quot;
    case $selection in
        1 ) clear ; vm_starter ;;
        2 ) default_options ; press_enter ;;
		3 ) list_vm ; press_enter ;;
		0 ) clear ; clean_up ; exit ;;
		* ) echo &quot;Please enter 1, 2, or 0&quot;
    esac
done

</pre>
</div></div>
		<!-- / message -->
		
<div style="float: left; margin:10px; width: 200px; margin-right: 5px;">
	<div class="smallfont" style="margin-bottom:2px">Code:</div>

	<pre class="alt2" dir="ltr" style="
		margin: 0px;
		padding: 6px;
		border: 1px inset;
		width: 640px;
		height: 500px;
		text-align: left;
		overflow: auto">#!/bin/bash 

#######################
# Author:phoenix122
# Version:1.0
#######################

# Turn on extended pattern matching for vm_starter function to work 
shopt -s extglob 

trap error_exit SIGHUP SIGINT SIGTERM

#############################################################
#############################################################

# Housekeeping, error handling, ease of use

function clean_up 
{
	# Perform Housekeeping
	# Accepts an exit status
	rm -f $TEMP_FILE ; rm -f $TEMP_FILE2
	exit $1
}


c

selection= 
vrde=&quot;--vrde off&quot; 

#### Constants
TEMP_FILE=$TEMP_DIR/vmh.$$.$RANDOM
TEMP_FILE2=$TEMP_DIR/vbhcom.$RANDOM.$$
PROGNAME=$(basename $0)

until [ &quot;$selection&quot; = &quot;0&quot; ]; do
    echo &quot;Virtual Machine Menu&quot;
	echo &quot;&quot;
    echo &quot;1 - Start a Virtual Machine with default options&quot;

    echo &quot;2 - Change default options&quot;
	echo &quot;3 - View current Virtual Machines&quot;
	echo &quot;&quot;
    echo &quot;0 - Exit&quot;
	echo &quot;&quot;

    echo -n &quot;Enter selection: &quot;
    read selection
    echo &quot;&quot;
    case $selection in
        1 ) clear ; vm_starter ;;
        2 ) default_options ; press_enter ;;
		3 ) list_vm ; press_enter ;;
		0 ) clear ; clean_up ; exit ;;
		* ) echo &quot;Please enter 1, 2, or 0&quot;
    esac
done

</pre>
</div></div>
		<!-- / message -->
```

---

