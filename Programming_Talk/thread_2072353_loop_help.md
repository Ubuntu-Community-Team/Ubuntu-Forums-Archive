---
title: "loop help"
date: 2012-10-17
forum: Programming Talk
---

### Post by bettaproger on 2012-10-17
I have the following script that works on single files, how do i make it run on the contents of a directory passed to the script as a command line argument. The loop keeps failing no matter what i try, please help. Note, this version is not the loops i have tried.
```

xbtfile() {
	if (( ! $#)); then
		printf 'usage: xbtfile (filename)' >&2
		return 1
	fi

	for f; do
		mencoder "$f" \
			-ovc xvid \
			-oac mp3lame \
			-xvidencopts bitrate=5000 \
			-lameopts abr:br=132 \
			-o "${f%.*}.xbox.avi"
	done
}
```

---

### Post by XplosS on 2012-10-19
I'm sure there will be more elegant solutions, but why don't you issue an "ls" in your code, and then use its results? :)

---

### Post by bettaproger on 2012-10-23
> **XplosS said:**
> I'm sure there will be more elegant solutions, but why don't you issue an "ls" in your code, and then use its results? :)

I'm honestly not sure how that would work but I did find a solution.
```

xbtdir() {
	if ((! $#)); then
		printf 'usage: xbtdir (directory)' >&2
		return 1
	fi

	for f in "$1"/*; do
#echo $1
		mencoder "$f" \
			-ovc xvid \
			-oac mp3lame \
			-xvidencopts bitrate=5000 \
			-lameopts abr:br=132 \
			-o "${f%.*}.xbox.avi"
		done
}
```

---

