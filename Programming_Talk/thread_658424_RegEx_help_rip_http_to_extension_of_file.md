---
title: "RegEx help: rip http:// to extension of file"
date: 2008-01-04
forum: Programming Talk
---

### Post by altonbr on 2008-01-04
I can't seem to figure out a way to find URLs with a certain extension via a webpage...

I've used:
```
/http:\/\/.\.pdf/
/http:\/\/.*\.pdf/
/http:\/\/()*\.pdf/
```
But I just can't seem to return all URLs that start with http:// and end with .pdf. How would I go about doing this?

---

### Post by bobbocanfly on 2008-01-04
```
/^http:\/\/.+\.pdf$/
```

Tested with

```
http://some.text.here.com/hElLo-WoRlD.pdf
```

---

### Post by altonbr on 2008-01-04
> **bobbocanfly said:**
> ```
/^http:\/\/.+\.pdf$/
```

Tested with

```
http://some.text.here.com/hElLo-WoRlD.pdf
```

Pretending this is the text:
```
$text='<link type="text/css" rel="stylesheet" href="http://wwwimages.adobe.com/www.adobe.com/lib/com.adobe/template/screen.css" media="screen" charset="utf-8" />
<link type="text/css" rel="stylesheet" href="http://wwwimages.adobe.com/www.adobe.com/lib/com.adobe/template/print.css" media="print" charset="utf-8" />
<link id="cs3-css" href="http://wwwimages.adobe.com/www.adobe.com/lib/com.adobe/template/devcenter/layout.css" type="text/css" rel="stylesheet" media="screen" />';
$protocol = 'http://';
$extension = '.css';
$pattern = '/'.preg_quote($protocol,'/').'.+'.preg_quote($extension,'/').'/';
preg_match_all($pattern, $text, $matches);
print_r($matches);
```

It won't return anything. If I change $pattern to:
```
$pattern = '/http:\/\//'
```
Then it returns 'http://' three times...

---

### Post by slavik on 2008-01-04
perl code:
```

$extension = "pdf";
$url = "http://some.text.here.com/hElLo-WoRlD.pdf"; #or whatever url you need
$file = $1 if (m|(http://.+?\.$extension)|);
print $file."\n";

```

EDIT: make php not be greedy by adding a ? (question mark) ...

---

### Post by altonbr on 2008-01-04
```
$text = ''; //cURL call to a website

$pattern1 = '/http:\/\//';
$pattern2 = '/http:\/\/.+\.pdf/';
$pattern3 = '/http:\/\/.+?\.pdf/';

preg_match_all($pattern1, $text, $matches1);
preg_match_all($pattern2, $text, $matches2);
preg_match_all($pattern3, $text, $matches3);
print_r($matches1);
print_r($matches2);
print_r($matches3);
```

```
Array
(
    [0] => Array
        (
            [0] => http://
            [1] => http://
            [2] => http://
            [3] => http://
            [4] => http://
            [5] => http://
            [6] => http://
            [7] => http://
            [8] => http://
            [9] => http://
            [10] => http://
            [11] => http://
            [12] => http://
            [13] => http://
            [14] => http://
            [15] => http://
            [16] => http://
            [17] => http://
            [18] => http://
            [19] => http://
            [20] => http://
            [21] => http://
            [22] => http://
        )

)
Array
(
    [0] => Array
        (
        )

)
Array
(
    [0] => Array
        (
        )

)
```

It still isn't grabbing everything from "http://" to ".pdf"...

---

### Post by slavik on 2008-01-04
try putting the regex inside parenthesis ...

---

### Post by bobbocanfly on 2008-01-04
The on i posted at the start works with [http://www.gregjackson.com/tools/regexpTester.htm](http://www.gregjackson.com/tools/regexpTester.htm). Dont know how it works but it works

---

### Post by slavik on 2008-01-04
forgot another thing ... set it to be global.

bob, the problem with you regex is that the url has to be the only thing in the line but the OP needs all the matches from a large text

---

### Post by altonbr on 2008-01-04
I applogize. It didn't work because of my ignorance.

The URLs containing the PDFs actually look like so:
> href="/devnet/pdf/pdfs/ISOFormatting_070604C.pdf"

What would be a regex that read anything inside the "" after href= if the file ends in .pdf?

---

### Post by bobbocanfly on 2008-01-04
> **altonbr said:**
> I applogize. It didn't work because of my ignorance.

The URLs containing the PDFs actually look like so:


What would be a regex that read anything inside the "" after href= if the file ends in .pdf?

Something like 

```
/href=".+\.pdf"/
```

might work. Not sure though, i started writing Regexes yesterday

---

### Post by ghostdog74 on 2008-01-04
```

    open(DATA,"file") or die "cannot open :$!";
    while (<DATA>) {
        {
            if ( $_ =~ /href="(.*\.pdf)"/ ) {
                print $1 . "\n";
            }
        }
    }
    close DATA;

```

---

### Post by altonbr on 2008-01-05
> **ghostdog74 said:**
> ```

    open(DATA,"file") or die "cannot open :$!";
    while (<DATA>) {
        {
            if ( $_ =~ /href="(.*\.pdf)"/ ) {
                print $1 . "\n";
            }
        }
    }
    close DATA;

```

Is that perl?

---

### Post by ghostdog74 on 2008-01-05
> **altonbr said:**
> Is that perl?

yes. if you are using php,  the regular expression is the same. 
```

$handle = fopen("file","r");
$pattern = '/href="(.*\.css)"/';
if ( $handle ) {
 while (  !feof($handle) ){
    $buffer=fgets($handle);
    preg_match($pattern,$buffer, $matches);
    print_r($matches);
 }
 fclose($handle);
}

```

---

### Post by altonbr on 2008-01-05
> **ghostdog74 said:**
> yes. if you are using php,  the regular expression is the same. 
```

$handle = fopen("file","r");
$pattern = '/href="(.*\.css)"/';
if ( $handle ) {
 while (  !feof($handle) ){
    $buffer=fgets($handle);
    preg_match($pattern,$buffer, $matches);
    print_r($matches);
 }
 fclose($handle);
}

```

Hey ghostdog74, that work perfectly! I'm much obliged...

One question though, how do I get it to return everything but [COLOR="DarkRed"]href="[/COLOR] and [COLOR="DarkRed"]"[/COLOR] via that RegEx?

I'm using strstr and substr functions right now to do the job, but is there a more efficient way to do it via RegExs?

Maybe this is time for you to suggest another book for me to read :P

---

### Post by altonbr on 2008-01-05
Alright sorry, I guess I'm getting confused...

preg_match_all() is returning two arrays.

One contains:
> href="/devnet/pdf/pdfs/HighlightFileFormat.pdf"

While the other contains:
> /devnet/pdf/pdfs/HighlightFileFormat.pdf

---

### Post by altonbr on 2008-01-05
Here's the script for anyone interested:
```
<?

/*
* Author: Ojas Ojasvi
* Released: September 25, 2007
* Modifier: Brett Alton
* Modified: January 04, 2008
* Description: An example of the disguise_curl() function in order to grab contents from a website while remaining fully camouflaged by using a fake user agent and fake headers.
* Original URL: http://ca3.php.net/manual/en/ref.curl.php#78046
*/

$url = 'http://www.adobe.com/devnet/pdf/pdf_reference.html';
$protocol = parse_url($url, PHP_URL_SCHEME).'://';
$domain = $protocol.parse_url($url, PHP_URL_HOST);
//$path = parse_url($url, PHP_URL_PATH);
$extension = 'pdf';
//$pattern = '/href=".+\.'.$extension.'"/';
$pattern = '/href="(.*\.'.$extension.')"/';

// disguises the curl using fake headers and a fake user agent.
function disguise_curl($url){
	$curl = curl_init();

	// Setup headers - I used the same headers from Firefox version 2.0.0.6
	$header[] = "Accept: text/xml,application/xml,application/xhtml+xml,text/html;q=0.9,text/plain;q=0.8,image/png,*/*;q=0.5";
	$header[] = "Cache-Control: max-age=0";
	$header[] = "Connection: keep-alive";
	$header[] = "Keep-Alive: 300";
	$header[] = "Accept-Charset: ISO-8859-1,utf-8;q=0.7,*;q=0.7";
	$header[] = "Accept-Language: en-us,en;q=0.5";
	$header[] = "Pragma: "; // browsers keep this blank.

	curl_setopt($curl, CURLOPT_URL, $url);
	curl_setopt($curl, CURLOPT_USERAGENT, 'Googlebot/2.1 (+http://www.google.com/bot.html)');
	curl_setopt($curl, CURLOPT_HTTPHEADER, $header);
	curl_setopt($curl, CURLOPT_REFERER, 'http://www.google.com');
	curl_setopt($curl, CURLOPT_ENCODING, 'gzip,deflate');
	curl_setopt($curl, CURLOPT_AUTOREFERER, true);
	curl_setopt($curl, CURLOPT_RETURNTRANSFER, 1);
	curl_setopt($curl, CURLOPT_TIMEOUT, 10);

	$html = curl_exec($curl); // execute the curl command
	curl_close($curl); // close the connection

	return $html; // and finally, return $html
}

// uses the function and displays the text off the website
$text = disguise_curl($url);

preg_match_all($pattern, $text, $matches, PREG_PATTERN_ORDER);
print_r($matches);

foreach ($matches as $set){
	foreach ($set as $link){
		if (preg_match('/'.preg_quote($domain,'/').'/',$link) != TRUE) {
			$link = $domain.$link;
		}
		print($link."\n");
	}
}

?>
```

---

### Post by ghostdog74 on 2008-01-05
> **altonbr said:**
> 
Maybe this is time for you to suggest another book for me to read :P
What else but the [PHP documentation ]("http://www.php.net/download-docs.php")? for a start? Download the chm version. Always handy when coding PHP.

---

