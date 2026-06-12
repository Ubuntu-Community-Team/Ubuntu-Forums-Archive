---
title: "retrieve xml  file using file_get_contents($request); too slow with unicode"
date: 2011-03-02
forum: Programming Talk
---

### Post by sdowney717 on 2011-03-02
I am trying to retrieve an xml file from a webservice.
I cant use the original server since it gags on non latin characters, unicode?, that is what the LOC says.

The other server does work with non latin characters
BUT it is too slow with file_get_contents, takes a minute to get anything, so slow you cant even use it in the program.
YET, retrieves the xml fast in the browser window.

So, what can I do that will work normally fast like it should?

```

//original database server, file_get_contents is faster, about 3 to 10 seconds
//$request= 'http://z3950.loc.gov:7090/voyager?version=1.1&operation=searchRetrieve'.$query.$test2.'&startRecord='.$offset.'&maximumRecords=20';

//new one that can handle non latin characters  
//file_get_contents is SLOW, so slow to be unusable, about a minute or more
$request='http://lx2.loc.gov:210/LCDB?version=1.1&operation=searchRetrieve'.$query.$test2.'&startRecord='.$offset.'&maximumRecords=20';


   $raw_xml = file_get_contents($request);
   $filename = dirname(__FILE__)."/loc.xml";
   $fp = fopen($filename, "w");
   fwrite($fp, $raw_xml);
   fclose ($fp);

```

---

### Post by sdowney717 on 2011-03-02
got it working fast using cURL
to get cURL working in ubuntu, install it

sudo apt-get install php5-curl

restart apache
sudo /etc/init.d/apache2 restart

this works very fast! why does it work so good compared to file_get_contents ?
[PHP]
$url = curl_get_file_contents($request);

function curl_get_file_contents($URL)
    {
        $c = curl_init();
        curl_setopt($c, CURLOPT_RETURNTRANSFER, 1);
        curl_setopt($c, CURLOPT_URL, $URL);
        $contents = curl_exec($c);
        curl_close($c);

        if ($contents) return $contents;
            else return FALSE;
    }

   $filename = dirname(__FILE__)."/loc.xml";
  //echo $raw_xml;
   $fp = fopen($filename, "w");
   fwrite($fp, $url);
   fclose ($fp);[/PHP]

---

