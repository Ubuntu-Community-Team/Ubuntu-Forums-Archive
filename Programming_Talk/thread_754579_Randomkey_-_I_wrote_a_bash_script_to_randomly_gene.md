---
title: "Randomkey - I wrote a bash script to randomly generate passwords and keys."
date: 2008-04-13
forum: Programming Talk
---

### Post by PR0M37H3U5 on 2008-04-13
I wasn't sure about the quality of random numbers coming out /dev/urandom and I don't like how /dev/random will block when read from, so I wrote a bash script. Randomkey hashes together random data from many different sources in your machine like network statistics, the list of running processes, kernel logs interrupts and much more. It ouputs a 64 character hash in hexadecimal format. You can use this as completely random 256 bit password or key. I use it for my [[COLOR="DarkSlateBlue"]Truewipe program[/COLOR]]("http://ubuntuforums.org/showthread.php?p=4710637")
The script stores it own manual within itself, to print you need [[COLOR="DarkSlateBlue"]extractor[/COLOR]]("http://ubuntuforums.org/showthread.php?p=4712387")

```

#Generates a random key by hashing data from many different sources within linux including urandom, kernel info, running processes, current memmory, the time and much more.

#Defaults
hash=sha256sum	#Hash method used
length=64	#Length of output in chars

print_usage() 
{ extractor -d -f $0 -t @manual@ ;}

#Get Options
while getopts 'h:il:s:' OPTION
do
  case $OPTION in
  h)	hash=$OPTARG;;
  i)	interactive=1;;
  l)	length=$OPTARG;;
  s)	seed=$OPTARG;;
  ?)	print_usage; exit 2;;
  esac
done
shift $(($OPTIND - 1))

if [ $1 ]; then seed=$1; fi

#Get Random Data
time=$(date +%N%s%u%w%Z)

#Generate list of commands:
#Creates the next section, edit commands in the sources section of this file:
#commands=$(\
#	echo "echo $( extractor randomkey @sources@ | sed 's/\n*/ $(/; s/$/ | $hash)/' | tr -d '\n')" )
#	pass=$( eval $commands | $hash )

#Get password
pass=$(\
echo $(dmesg | $hash) $(cat /proc/cpuinfo | $hash) $(cat /proc/meminfo | $hash) $(cat /proc/interrupts | $hash) $(cat /proc/stat | $hash) $(cat /proc/iomem | $hash) $(cat /proc/ioports | $hash) $(cat /proc/mounts | $hash) $(lshal | $hash) $(free -b | $hash) $(vmstat -s | $hash) $(vmstat -d | $hash) $(tail -n 500 /var/log/messages | $hash) $(id | $hash) $(last | $hash) $(who | $hash) $(groups | $hash) $(ps -aefw | $hash) $(fuser -mv / 2>&1 | $hash) $(netstat -s | $hash) $(route -n | $hash) $(dd if=/dev/urandom bs=256 count=4 2>&1 | $hash) \
| $hash )


if [ $interactive ]; then
	echo "Type Randomly:"
	read seed
fi

time=$(echo \
	$time\
	$(date +%N%s%u%w%Z) \
	$(dd if=/dev/urandom bs=256 count=4 2>&1 | $hash -b)\
	| $hash)

#Output Random Key
echo $time $pass $seed | $hash | head -c $length

#Wipe Vars
pass=$(echo | $hash)
time=$(echo | $hash)
pass=""
time=""

exit 0

#random sources
#some commands found at http://cb.vu/unixtoolbox.xhtml

@sources@

#Hardware Information
dmesg	#Detected hardware and boot messages
cat /proc/cpuinfo  	# CPU model
cat /proc/meminfo  	# Hardware memory
cat /proc/interrupts	# interrupts
cat /proc/stat
cat /proc/iomem
cat /proc/ioports
cat /proc/mounts
lshal  			# Show a list of all devices with their properties

#Memory
free -b
vmstat -s
vmstat -d

#Load, statistics and messages
tail -n 500 /var/log/messages      # Last 500 kernel/syslog messages
#Users
id                                 # Show the active user id with login and
last                               # Show last logins on the system
who                                # Show who is logged on the system
groups

#Processes
ps -aefw                         # Extensive list of all running process
fuser -mv / 2>&1		 # Find opened files by processes

#Network
netstat -s                # System-wide statistics for each network protocol
route -n		  # Print routing table

#urandom
dd if=/dev/urandom bs=256 count=4 2>&1

@sources@
@manual@
Usage:	randomkey [options] seed

Optional:
	-h hash method (default sha256sum)
	-i interactive mode
	-l maximum length of the key
	-s seed (random characters provided by you, not required)

Examples:
	#Print a 64 character random key
	randomkey
	
@manual@


```

Note: extractor was also used to produce some of the code in this program.

---

