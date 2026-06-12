---
title: "Download a file in c using curl"
date: 2010-11-16
forum: Programming Talk
---

### Post by Woody1987 on 2010-11-16
I have some C code using curl that I want to use to download a csv file. When I use it though, instead of getting and writing the file to disk, it writes the HTML of the webpage. Here is my code:

```

size_t my_write_func(void *ptr, size_t size, size_t nmemb, FILE *stream)
{
    return fwrite(ptr, size, nmemb, stream);
}

void *downloadFile(void *ptr)
{
    CURL *curl;
    CURLcode res;
    FILE *outfile;
    char *symbol = (char *)ptr;

    curl = curl_easy_init();
    if(curl)
    {
        outfile = fopen(symbol, "w");
        char url[100] = "http://finance.yahoo.com/d/quotes.csv?s=";
        strcat(url, symbol);
        strcat(url, "&f=npl1");
        curl_easy_setopt(curl, CURLOPT_URL, url);
        curl_easy_setopt(curl, CURLOPT_WRITEDATA, outfile);
        curl_easy_setopt(curl, CURLOPT_WRITEFUNCTION, my_write_func);

        res = curl_easy_perform(curl);
        curl_easy_cleanup(curl);
        fclose(outfile);
    }
}

```


Thanks.

---

### Post by r-senior on 2010-11-16
When you say the HTML of the web page, is it an error message of some sort? Such as you would get with a 404 Not Found or 403 Access Denied type response, for example?

Or is it some other page?

---

### Post by Arndt on 2010-11-16
> **Woody1987 said:**
> I have some C code using curl that I want to use to download a csv file. When I use it though, instead of getting and writing the file to disk, it writes the HTML of the webpage. Here is my code:

```

size_t my_write_func(void *ptr, size_t size, size_t nmemb, FILE *stream)
{
    return fwrite(ptr, size, nmemb, stream);
}

void *downloadFile(void *ptr)
{
    CURL *curl;
    CURLcode res;
    FILE *outfile;
    char *symbol = (char *)ptr;

    curl = curl_easy_init();
    if(curl)
    {
        outfile = fopen(symbol, "w");
        char url[100] = "http://finance.yahoo.com/d/quotes.csv?s=";
        strcat(url, symbol);
        strcat(url, "&f=npl1");
        curl_easy_setopt(curl, CURLOPT_URL, url);
        curl_easy_setopt(curl, CURLOPT_WRITEDATA, outfile);
        curl_easy_setopt(curl, CURLOPT_WRITEFUNCTION, my_write_func);

        res = curl_easy_perform(curl);
        curl_easy_cleanup(curl);
        fclose(outfile);
    }
}

```


Thanks.

Have you checked that 'url' does indeed contain the string you want, and that fetching it with an external tool such as 'wget' gets what you expect?

---

### Post by Woody1987 on 2010-11-17
Take for example this address:
[http://finance.yahoo.com/d/quotes.csv?s=msft&f=npl1]("http://finance.yahoo.com/d/quotes.csv?s=msft&f=npl1")

In firefox it downloads an CSV from yahoo which should contain some stock info, but in this program it downloads:

```

<HEAD><TITLE>Redirect</TITLE></HEAD>					
<BODY	BGCOLOR="white"	FGCOLOR="black">			
<FONT	FACE="Helvetica,Arial"><B>				
	<em>http://download.finance.yahoo.com/d/quotes.csv?s=msft&f=npl1</em>.<p></B></FONT>				
					
<!--	default	Redirect	response	(301)	-->
</BODY>					

```

I have had this working correctly in Android Java using:

```

URL url = new URL("http://finance.yahoo.com/d/quotes.csv?s=" + symbol + "&f=npl1");
HttpURLConnection connect = (HttpURLConnection) url.openConnection();
connect.setRequestMethod("GET");
connect.setDoOutput(true);
connect.connect();
		
FileOutputStream output = ctx.openFileOutput(symbol + ".txt", Context.MODE_WORLD_READABLE);
InputStream input = connect.getInputStream();
		
int downloadSize = 0;
		
byte buffer[] = new byte[1024];
int bufferLength = 0;
		
while((bufferLength = input.read(buffer)) > 0)
{
	output.write(buffer, 0, bufferLength);
	downloadSize += bufferLength;
}
		
output.close();

```

---

### Post by Arndt on 2010-11-17
> **Woody1987 said:**
> Take for example this address:
[http://finance.yahoo.com/d/quotes.csv?s=msft&f=npl1]("http://finance.yahoo.com/d/quotes.csv?s=msft&f=npl1")

In firefox it downloads an CSV from yahoo which should contain some stock info, but in this program it downloads:

```

<HEAD><TITLE>Redirect</TITLE></HEAD>					
<BODY	BGCOLOR="white"	FGCOLOR="black">			
<FONT	FACE="Helvetica,Arial"><B>				
	<em>http://download.finance.yahoo.com/d/quotes.csv?s=msft&f=npl1</em>.<p></B></FONT>				
					
<!--	default	Redirect	response	(301)	-->
</BODY>					

```

I have had this working correctly in Android Java using:

```

URL url = new URL("http://finance.yahoo.com/d/quotes.csv?s=" + symbol + "&f=npl1");
HttpURLConnection connect = (HttpURLConnection) url.openConnection();
connect.setRequestMethod("GET");
connect.setDoOutput(true);
connect.connect();
		
FileOutputStream output = ctx.openFileOutput(symbol + ".txt", Context.MODE_WORLD_READABLE);
InputStream input = connect.getInputStream();
		
int downloadSize = 0;
		
byte buffer[] = new byte[1024];
int bufferLength = 0;
		
while((bufferLength = input.read(buffer)) > 0)
{
	output.write(buffer, 0, bufferLength);
	downloadSize += bufferLength;
}
		
output.close();

```

There is an option CURLOPT_FOLLOWLOCATION. Have you tried setting it to 1? (I haven't used curl in any form - I just googled a bit.)

---

### Post by pradeepthundiyil on 2010-11-17
hi,

I have done a code using curl in VC++ using MS visual studio 2010. I have uploaded the same in 

[http://www.planet-source-code.com/vb/scripts/ShowCode.asp?txtCodeId=13318&lngWId=3](http://www.planet-source-code.com/vb/scripts/ShowCode.asp?txtCodeId=13318&lngWId=3)

You can have a look..

---

### Post by Woody1987 on 2010-11-17
> **Arndt said:**
> There is an option CURLOPT_FOLLOWLOCATION. Have you tried setting it to 1? (I haven't used curl in any form - I just googled a bit.)

Yay, thankyou, that worked.

---

### Post by paddy1008 on 2011-12-09
How to get HTTP for given IP?

How to set HTTP header HOST:<field>  Contentype in req.

and get the error info?

Best regards,
Paddy.

---

### Post by paddy1008 on 2011-12-12
Can anyone help me out to get Content lenght of downloaded file by using

curl_easy_getinfo(curl,CURLINFO_CONTENT_LENGTH_DOWNLOAD, &double_int)


Best regards,
paddy1008

---

### Post by paddy1008 on 2011-12-12
As above command returing content len as ZERO

evenif content len is ~2000.

-paddy1008.

---

