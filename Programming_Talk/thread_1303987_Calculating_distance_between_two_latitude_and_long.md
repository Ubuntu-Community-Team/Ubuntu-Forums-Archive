---
title: "Calculating distance between two latitude and longitude positions"
date: 2009-10-28
forum: Programming Talk
---

### Post by tom66 on 2009-10-28
I'm trying to calculate a distance from two latitude and longitude positions. However, I keep getting strange 4,000 km+ results, when I should be getting around 11 km. 

I'm using the following PHP function:

[php]function estimate_distance_crow_flies($lat1, $lon1, $lat2, $lon2)
{
    return acos(sin(deg2rad($lat1)) * sin(deg2rad($lat2)) + cos(deg2rad($lat1)) * cos(deg2rad($lat2)) * cos(deg2rad($lon2 - $lon1))) * 6371;
}[/php]

With the following values:
Lat		Long
0.313611	32.581111	Kampala, Uganda
0.397222	32.638889	Kira, Uganda

I can verify it from the internet, that it should be about 11 km:

[http://www.movable-type.co.uk/scripts/latlong.html](http://www.movable-type.co.uk/scripts/latlong.html)

(and also a map and a ruler)

So I suspect something's wrong with my formula, but what? This error occurs for different values, as well.

Help much appreciated...

---

### Post by geirha on 2009-10-28
```

$ cat /tmp/test.php
<?php
function estimate_distance_crow_flies($lat1, $lon1, $lat2, $lon2)
{
    return acos(sin(deg2rad($lat1)) * sin(deg2rad($lat2)) + cos(deg2rad($lat1)) * cos(deg2rad($lat2)) * cos(deg2rad($lon2 - $lon1))) * 6371;
}  
echo estimate_distance_crow_flies(0.313611, 32.581111, 0.397222, 32.638889);
?>
$ php /tmp/test.php 
11.3009103409

```

Looks right to me. Maybe you're passing the arguments in the wrong order?

---

### Post by tom66 on 2009-10-28
Of course, why didn't I think of that.

Yeah, I'd swapped the args such that instead of (lat1, lon1, lat2, lon2) I had (lat1, lat2, lon1, lon2). 

Bed time, I'm not thinking straight... that bug had me for an hour.

Thanks for your help now I can sleep.

---

