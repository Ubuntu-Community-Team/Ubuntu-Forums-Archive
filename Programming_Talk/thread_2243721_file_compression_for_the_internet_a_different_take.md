---
title: "file compression for the internet a different take"
date: 2014-09-10
forum: Programming Talk
---

### Post by terramir on 2014-09-10
Someone suggested this before but that thread is closed, and I thought this out a bit more than b4. Not sure of the processing power needed though.
take any file larger than 1kb and get a checksum with one method, now if you have this checksum for 8192^2 or more combinations you have boiled the possible file content down to maybe 50 to 1000 different combinations that can have the same checksum, if you use a different method on the original file as well the overlapping matches should reduce them selves to maybe 100 different iterations, now using five to ten different algorithms you should be ably to dynamically reduce this to one distinct possible combination so let's say computer one takes in video file A 700mb the software using as many different algorithms in a specific order until there are only let's say 3 to 10 possibilities and then writes a file with the (however many different checksums plus how many left overs and which one it would be if the same order is followed and the other computer should be able to write out exactly that original file based on the data provided. 
the question is how many checksums would be needed, and how much computing power would be needed to extrapolate based on the information given. if you eliminate all other possibilities what's left however improbable must be the truth or the file in this case. 
Now is this feasible or would you need a quantum computer to reconstruct based on this kind of data?
terramir

---

