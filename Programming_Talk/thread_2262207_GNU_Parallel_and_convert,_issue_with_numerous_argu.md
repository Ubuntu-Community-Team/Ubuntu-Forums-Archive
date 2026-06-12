---
title: "GNU Parallel and convert, issue with numerous arguments"
date: 2015-01-23
forum: Programming Talk
---

### Post by Scooby-2 on 2015-01-23
I have a bash script which locates all jpg images in a directory and stamps each one with the date and time of the files' creation time in the top left corner using convert. The line in my script is:


```
convert "${file}" -gravity NorthWest -pointsize 14 -undercolor '#00000080' -fill yellow -annotate +0+20 "$(date -r ${file} +'%d-%m-%y %H:%M:%S')" ${stamped_dir}/frame"$(basename ${file})"_stamped.jpg

```

where $file is assigned to each jpg to be processed. I wrote bash functions to determine the files' creation date but soon realised that these cannot be called from within parallel, so I wrote a bash script to create a file called jpglist to be used. It contains the path and file name, a tab, then the timestamp for that file, then a new line for the next entry. So each line of this file looks something like this:


> 2015-01-17--00h-00m/frame00001.jpg    17-01-15_08:00:04
     .
     .
2015-01-17--00h-00m/frame00015.jpg    19-01-15_09:00:06


The entries are tab-separated. With Parallel, I have tried a multitude of permutations something like the following:


```
cat jpglist | parallel --gnu -v --colsep '\t' "convert -gravity NorthWest -pointsize 14 -undercolor '#00000080' -fill yellow -annotate +0+20" {1} -write {2} {1}.JPG

```

However, parallel seems to be awkward about convert and the arguments it needs. The double quotes are there because without them I make even less headway! Here's the output from the above command with 2 jpg files listed in the jpglist:


> convert -gravity NorthWest -pointsize 14 -undercolor '#00000080' -fill yellow -annotate +0+20 ./2015-01-19--09h-00m/frame00001.jpg -write 19-01-15_09:00:00 ./2015-01-19--09h-00m/frame00001.jpg.JPG
convert.im6: no images defined `./2015-01-19--09h-00m/frame00001.jpg.JPG' @ error/convert.c/ConvertImageCommand/3044.
convert -gravity NorthWest -pointsize 14 -undercolor '#00000080' -fill yellow -annotate +0+20 ./2015-01-19--09h-00m/frame00015.jpg -write 19-01-15_09:00:06 ./2015-01-19--09h-00m/frame00015.jpg.JPG
convert.im6: no images defined `./2015-01-19--09h-00m/frame00015.jpg.JPG' @ error/convert.c/ConvertImageCommand/3044.


I am running GNU parallel 20141122 on Linux Mint 17. I know my jpglist file is OK as the following works:


```
cat jpglist | parallel --gnu --colsep '\t' echo "frame={1}, timestamp={2}"

```

The output is:


> 2015-01-17--00h-00m/frame=frame00001.jpg, timestamp=19-01-15_09:00:00
2015-01-17--00h-00m/frame=frame00015.jpg, timestamp=19-01-15_09:00:06


My question is: Can convert be used in this way with GNU Parallel? Processing 25,000 files one at a time takes bash around half an hour and as I have 4 cores I was hoping to be able to reduce this.

---

### Post by Holger_Gehrke on 2015-01-24
> **Scooby-2 said:**
> 
```
cat jpglist | parallel --gnu -v --colsep '\t' "convert -gravity NorthWest -pointsize 14 -undercolor '#00000080' -fill yellow -annotate +0+20" {1} -write {2} {1}.JPG

```


Seems to me the problem is the space between {1} and {2}. convert 'thinks' {2} is the complete argument to '-write' and {1} is another file to convert ...

> **Scooby-2 said:**
> 
My question is: Can convert be used in this way with GNU Parallel? Processing 25,000 files one at a time takes bash around half an hour and as I have 4 cores I was hoping to be able to reduce this.

Depends on processor speed, disk speed and your input data. If most of the half hour is spend on file IO, then parallel won't help at all. The more time is needed for the actual processing, the more help will parallel execution be.

---

### Post by ofnuts on 2015-01-24
Not really answering the question, but using the current file date isn't a very reliable way to timestamp a picture. If these come from a camera, the timestamp of the actual shot is included in the Exif metadata in the file (see exiftool to extract/edit values). But then timestamping the image itself is of little value since the Exif data can be retrieved/displayed by any photo software worth its salt (Gwenview and others). and you avoid damaging the original picture with a timestamp.

---

### Post by Scooby-2 on 2015-01-25
@[COLOR=#000000]Holger_Gehrke

[/COLOR]Thanks for the response.

I agree that convert's problem is deciding what the parameters are. However, the parallel command with the -v switch echoes the correct convert syntax, as I put in the original post, namely
> [COLOR=#000000]*convert -gravity NorthWest -pointsize 14 -undercolor '#00000080' -fill yellow -annotate +0+20 ./2015-01-19--09h-00m/frame00001.jpg -write 19-01-15_09:00:00 ./2015-01-19--09h-00m/frame00001.jpg.JPG*[/COLOR]
This works perfectly on the command line under bash. But not with GNU parallel.

---

### Post by Scooby-2 on 2015-01-25
@ofnuts

Thanks for the reply.

I agree that using a file's time stamp may not always be the best way of determining its creation time. However in my case it's the only way, as I am using an Rpi to capture still images from a webcam (the Rpi syncs to an NTP server). However, the webcam does not stamp the frames nor write EXIF data, hence my need to stamp each frame manually. The Pi takes around 6 frames a second which is sufficient for video creation. While running convert, the CPU is running at 100% and I/O is nowhere near max'd out. If parallel were to be usable, I appreciate that running 8 concurrent processes under parallel would probably push my PC to being I/O bound, but as it's easy to limit the number of concurrent jobs that parallel runs, I could find a balance if only it would run the command correctly.

---

