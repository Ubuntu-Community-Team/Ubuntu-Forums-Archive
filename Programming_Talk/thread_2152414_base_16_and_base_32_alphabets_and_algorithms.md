---
title: "base 16 and base 32 alphabets and algorithms"
date: 2013-06-07
forum: Programming Talk
---

### Post by osx on 2013-06-07
This, I'm sure, will be a strange question. I've already searched it out on the Internet and can't find the answer, but I really don't even know what the best keywords are to search for given the unusual nature of the matter.

The project would take too long to explain it all, plus I am not able to, but here is the short of it.

We're storing hashes of data strings (has nothing to do with passwords or any sort of confidential data) specific to an organization. All I can say is it has to do with intellectual property.

They want the data stored in a variety of hashes (has to do with speed and collision detection depending on the application), two of which are MD5 and SHA1. However, the SHA1 will be stored in base 32, not the usual base 16. It makes absolutely no sense to me to do it this way and I can't get an answer as to why, but it is not something I can change unless the following is true.

Since an MD5 is 32 *characters* long, and a SHA1 in base 32 is also 32 *characters* long, is there a chance that an MD5 could match a SHA1 in base 32 even though the two formats use a different alphabet set?

My argument is that there may be a false hit on a SHA1 stored in base 32 when an MD5 is being searched.

Thanks for any help.

---

### Post by davetv on 2013-06-07
Yes there is a chance but it is more than extremely minute at (by my calculation 1/2^256) or 1 in 1.1579209e+77.  I don't think this is anything to worry about.

---

### Post by osx on 2013-06-07
> **davetv said:**
> Yes there is a chance but it is more than extremely minute at (by my calculation 1/2^256) or 1 in 1.1579209e+77.  I don't think this is anything to worry about.

Thanks, davetv.

I suppose one could calculate the number of possible SHA1 base 32 hashes which contain only the possible base 16 values. I'm not quite sure how to do that, but maybe I could dig up my old statistical books from college and do it.

I think you would need to calculate all possible combinations, of exactly 32 character lengths, using the characters: 2, 3, 4, 5, 6, 7, A, B, C, D, E, F.

Then calculate the percentage of that number to the total possible number of MD5 values? Sound about right?

Thanks.

---

### Post by ofnuts on 2013-06-08
SHA1 is 40 hex digits. SHA256 is 64 hex digits.

Whatever the encoding of the SHAxxx, there are still 2^128 32-hex-digit-numbers so the chances of collision with something else are still abysmally low, and at least as low as the chances to get a false hit between two MD5 hashes.

---

### Post by osx on 2013-06-10
By my calculations, there are approximately 3,418,218,918,720,000,000,000,000,000,000,000,000,000,000,000 overlapping values. Since the system is not looking at random data, I'm not sure if that would increase or decrease the likelihood of a false hit.

I guess I'll just put the numbers out there to the people that make the decisions and see what they decide. If something goes wrong, at least it will be on them and not me.

---

