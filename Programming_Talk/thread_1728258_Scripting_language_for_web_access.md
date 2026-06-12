---
title: "Scripting language for web access"
date: 2011-04-13
forum: Programming Talk
---

### Post by cpgos on 2011-04-13
Could somebody please suggest a scripting language that can be used to download sequentially numbered files from a website.

For example, if a website makes available 20 chapters of a book as pdf files arranged as [www.anysite.com/chapter1.pdf](www.anysite.com/chapter1.pdf), [www.anysite.com/chapter2.pdf](www.anysite.com/chapter2.pdf), [www.anysite.com/chapter3.pdf](www.anysite.com/chapter3.pdf) etc is there a scripting language that can be used to sequentially download them. This avoids having to do so manually.

Best regards,
cpgos

---

### Post by Some Penguin on 2011-04-13
Just about anything.  Even tcl seems to have http-client modules available these days.  I'd personally use Perl, but that's because I'm very familiar with it including with various web-crawling packages for it; it's not a claim that Perl is superior to other languages for this purpose.

---

### Post by Reiger on 2011-04-13
If you know the URL pattern in advance and it is the raw files you want I would use shell scripts for this because it's a simple for loop around a wget command. Robust networking for a mere 3 lines of code on your part, can't get much easier than that.

If on the other hand you need to discover exactly how many chapters by parsing out some table of contents, say, it gets a bit more tricky. Again if you know a lot about anysite.com, shell scripting is still a good choice. But if you need to do fairly complex queries on a HTML page, you may want to look for an environment that has these two things:

[list]
[*]A good (X)HTML parser, or bindings to a library which does that. Depending on the website you want to download from you may require a rather flexible parser or can get by with one that is less tolerant of errors in the markup.
[*]A good HTTP library or bindings to one for instance cURL. After all, you probably don't want to implement timeouts and retries, redirects, error handling and so on and so forth.
[/list]

It doesn't really mater which language you choose here because you basically wire a few library calls together.

---

### Post by NFblaze on 2011-04-13
As was said earlier you could probrably use bash to do all of this. With utilities such as wget or curl. 

Though, if you prefer a language. Im not a genius, but I was looking at the python http library and it was pretty simple to follow.

Also, many people say PHP is simple.

---

### Post by BkkBonanza on 2011-04-13
One line at the console using bash,

for x in {1..20}; do wget www.anysite.com/chapter$x.pdf; done

---

### Post by cpgos on 2011-04-13
Thank you all for your responses.

As the final one seems to be the simplest I will try that first. Also, I will investigate what is involved in using Python, PHP and Perl.

Best regards,
cpgos

---

### Post by cgroza on 2011-04-13
Ruby, Python...

---

### Post by An Sanct on 2011-04-14
If you have LAMP, you could use PHP

[PHP]
<?php

function DownloadUrl($Url){
    if (!function_exists('curl_init')){ 
        die('CURL is not installed!');
    }
    $ch = curl_init();
    curl_setopt($ch, CURLOPT_URL, $Url);
    curl_setopt($ch, CURLOPT_REFERER, "http://www.google.com/");
    curl_setopt($ch, CURLOPT_USERAGENT, "MozillaXYZ/1.0"); original in the sample
    curl_setopt($ch, CURLOPT_HEADER, 0); //Minefield :)
    curl_setopt($ch, CURLOPT_RE==URNTRANSFER, true);
    curl_setopt($ch, CURLOPT_TIMEOUT, 10);
    $output = curl_exec($ch);
    curl_close($ch);
    return $output;
}

function DownIT($UrlPrefix, $UrlSuffix, $IntFrom, $IntTo){

for ($i = $IntFrom; $i <= $IntTo; $i++) {
    $rawdata = DownloadUrl($UrlPrefix.$i.$UrlSuffix);
        file_put_contents('downloaded'.$i.$UrlSuffix, $rawdata);

    }
}

//now here just call something like
// sample for 'samplesite.com/download/example[1..12]m.jpg'
// DownIT('samplesite.com/download/example', 'm.jpg', 1, 12); 
?>
[/PHP]I also agree, that PHP is not the extremely best way to go, so is no other language ... the point is to use what you have present, may it be javascript/html/php/asp/c++/bash.....
If the result are downloaded files, they all do the same: "good enough" :)

PS. typos and errors may be present, I haven't tested this script ... tweak it to your taste ;)

---

### Post by Blackbug on 2011-04-15
well probably wget is the best and simple thing for this.
wget -e robots=off -r -l1 --no-parent -A.pdf http://<site-name>
 
curl is other option...

---

### Post by cpgos on 2011-04-23
Using wget was suitable for nearly everything that I wanted to do.

The only complications that arose were some of the sites occasionally used the letter "o" when a zero was intended, which generated an error.

Thanks again for all the helpful responses.

Best regards,
cpgos

---

