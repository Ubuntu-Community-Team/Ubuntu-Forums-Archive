---
title: "replaygain shell script"
date: 2009-03-04
forum: Programming Talk
---

### Post by poguemahone on 2009-03-04
I have a shell script (see below) that I am using to assign replaygain tags to my music collection.  I didn't write the script, I just copied it from another website.  When I run this shell script (./replaygain.sh) I get the following errors:

[INDENT]/media/bigdog/Scripts/replaygain.sh: 9: [[: not found
/media/bigdog/Scripts/replaygain.sh: 15: [[: not found
/media/bigdog/Scripts/replaygain.sh: 22: [[: not found
/media/bigdog/Scripts/replaygain.sh: 22: 0: not found
/media/bigdog/Scripts/replaygain.sh: 30: [[: not found[/INDENT]

Any ideas why this doesn't work? Am I using the wrong shell?


```
#!/bin/sh

LC_NUMERIC=POSIX; export LC_NUMERIC

MP3GAIN=`which mp3gain`
if [[ $? != 0 ]]; then
	echo "mp3gain executable not found." >&2
	exit 1
fi

EYED3=`which eyeD3`
if [[ $? != 0 ]]; then
	echo "eyeD3 executable not found." >&2
	exit 1
fi

if [[ $# > 1 || $# == 1 && $1 != "-f" ]]; then
	echo "Usage: `basename $0` [-f]" >&2
	echo " for ReplayGain'ing all mp3 file into current directory" >&2
	echo " -f -- force re-ReplayGain'ing for already ReplayGain'ed files" >&2
	exit 2
fi

if [[ $# == 0 ]]; then
	$EYED3 --no-color *.mp3 | egrep -i '^UserTextFrame: \[Description: replaygain_album_gain\]$' >/dev/null 2>&1
	if [[ $? == 0 ]]; then
		echo "Files already ReplayGain'ed." >&2
		exit 1
	fi
fi

# files have not been ReplayGain'ed, so do all files in directory
#
# add custom switches?
# -c ignore clipping warning
$MP3GAIN *.mp3

TMPFILE=`tempfile`

for n in *.mp3; do
	# -s c - only check stored tag info (no other processing)
	# output tags to TMPFILE
	$MP3GAIN -s c "$n" > $TMPFILE
	
	#-s d - delete stored tag info (no other processing)
	$MP3GAIN -s d "$n"

	# read tags from TMPFILE
	TRACK_GAIN=`awk '/^Recommended "Track" dB / { printf("%+.2f dB", $5) }' $TMPFILE`
	ALBUM_GAIN=`awk '/^Recommended "Album" dB / { printf("%+.2f dB", $5) }' $TMPFILE`
	TRACK_PEAK=`awk '/^Max PCM / { printf("%.6f", $7/32768) }' $TMPFILE`
	ALBUM_PEAK=`awk '/^Max Album PCM / { printf("%.6f", $8/32768) }' $TMPFILE`
	
	# write tags
	$EYED3 \
	--set-user-text-frame="replaygain_track_gain:$TRACK_GAIN" \
	--set-user-text-frame="replaygain_track_peak:$TRACK_PEAK" \
	--set-user-text-frame="replaygain_album_gain:$ALBUM_GAIN" \
	--set-user-text-frame="replaygain_album_peak:$ALBUM_PEAK" \
	"$n"
done

rm -f $TMPFILE

```

---

### Post by ghostdog74 on 2009-03-04
change "#!/bin/sh" at the top of your file to #!/bin/bash (or where your bash is located)

---

### Post by poguemahone on 2009-03-04
Thank you!

---

