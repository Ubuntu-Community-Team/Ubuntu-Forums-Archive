---
title: "Obejct-Oriented PHP help"
date: 2011-02-19
forum: Programming Talk
---

### Post by skytreader on 2011-02-19
I made a class

[PHP]
Class UrlBridge{
	private $homefolder_regex;
	private $homeindex;
	private $distance;
	
	function __constructor($homefolder){
		print "Creating UrlBridge";
		$this->homefolder_regex = $homefolder;
		$currentFolder = getcwd();
		$this->homeindex = getIndex($homefolder, explode("/", currentFolder));
		$this->distance = $this->homeindex - count($currentFolder);
		echo "homeindex - count = $this->distance<br />";
	}
	
	function getIndex($search_regex, $search_array){
		$i = 0;
		$limit = len($search_array);
		
		while($i < $limit){
			if(preg_match($search_regex, $search_array[$i])){
				return $i;
			}
			
			$i++;
		}
		
		return -1;
	}
	
	function getDistance(){
		return $this->distance;
	}
	
	function getDots(){
		$i = 0;
		$limit = $this->distance;
		$dots = "";
		echo "The limit is $limit <br />";
		while($i < $limit){
			$dots .= "../";
			$i++;
		}
		echo "Returning $dots";
		return $dots;
	}
}
[/PHP]

and then somewhere in my code, I do

[PHP]$distance_finder = new UrlBridge("/some regexes here/");
	$dots = $distance_finder->getDots();[/PHP]

and then call them to import some javascript files like

[PHP]function echo_js($jsfile){
	echo "<script type='text/javascript' language='javascript' src='$jsfile'></script>";
}


echo_js($dots . "boilerplate/js/url_distance.js");
echo_js($dots . "boilerplate/js/header.js");
[/PHP]

Problem is, all I get (from my debugging echos---I don't expect visible stuff from echo_js, of course):

> The limit is 
Returning

which all came from getDots. I notice that there are no values indicated. Also, my debugging echos from __constructor are not showing.

Anything I'm missing?

---

### Post by sneakyimp on 2011-02-19
I believe it's __construct, not __constructor.  Try fixing that and see if it helps?

---

### Post by skytreader on 2011-02-20
Ouch. What a facepalm error. Thanks sneakyimp!

---

