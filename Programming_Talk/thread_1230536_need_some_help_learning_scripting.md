---
title: "need some help learning scripting"
date: 2009-08-03
forum: Programming Talk
---

### Post by BufordPants on 2009-08-03
I want to develop a bash procedure called createTestMP3Files() that creates a subdirectory named TESTMP3 in the current working directory, and populates it with about a 100 dummy MP3 files.

This creates one dummy mp3 file.

createOneDummyMP3File()
{
echo > $1.mp3
id3tool $1.mp3 -a $2 -r $3 -y $4
}

Any help would be greatly appreciated!

---

### Post by djurny on 2009-08-03
```
#!/bin/bash

RET=0

create_dummy_mp3_files() {
	local ret=0			# return value
	local dir=${1:-./TESTMP3}	# function parameter default is ./TESTMP3
	local number=${2:-100}		# function parameter default is 100
	local counter			# counter
	local dummy			# filename of dummy mp3 file

	mkdir -p $dir || ret=$?
	pushd $dir >/dev/null || ret=$?

	# use 'seq' to generate a sequence of 1 .. $number
	for counter in $(seq 1 $number); do
		# create a dummy mp3 file using mktemp
		dummy=$(mktemp -p $dir XXXXX)

		# create a tag for dummy mp3 file
		id3tool \
			-a="album #$counter" \
			-r="the artist formerly known as #$counter" \
			-y="$((2000 + $counter))" \
			$dummy

		mv $dummy $dummy.mp3 || ret=$?

		[ $ret -gt 0 ] && break
	done
	
	popd >/dev/null
	return ${ret}
}

echo "hi there"

create_dummy_mp3_files /tmp/testmp3s 50
RET=$?

if [ $RET -gt 0 ]; then
	echo "oops! something went wrong.."
fi

echo "bye now!"

exit $RET

# EOF

```

mixture of all kinds of things bash :)

hope this helps..

---

