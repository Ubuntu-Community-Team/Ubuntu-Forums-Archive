---
title: "PHP object array question"
date: 2009-01-01
forum: Programming Talk
---

### Post by hydrogen18 on 2009-01-01
Is it possible to create an array of objects in PHP? I seem to be able to do it successfully in a statically referenced way like 

```

$myobj[3] = new object("Hi!");

```

However in this snippet of code where I am accessing a portion of the array based on a variable specifying an index I get an error of 

```

Fatal error: Call to a member function getTextHTMLlink() on a non-object in /var/www/navmenu.php on line 22
```

Here is the code with the associated line in bold

```

<?php
class navMenu{
	protected $numItems=-1;
	protected $items=array();
	protected $title=0;
	
	function __construct($ptitle){
		$this ->title = $ptitle;
	}
	
	function addItem($itemTitle, $itemUrl){
	$this->numItems++;
	echo "navMenuItem added! numItems is now " . $this->numItems;
	$this->items[$this->numitems] = new navMenuItem($itemTitle,$itemUrl);
	} //additem
	
	function toHTMLTable(){
		$table = "<table><tr><td>" . $this->title . "</td></tr>";
		
		for($counter=0; $counter<=$this->numItems;$counter++){
			$table .= "<tr><td>";
			$table .= **$this->items[$counter]->getTextHTMLlink()**;
			$table .= "</td></tr>";

		}
		
		$table .= "</table>";
		return $table;
		}
}

class navMenuItem{
	protected $text=0;
	protected $url=0;
	protected $imageUrl=0;
	
	function __construct($ptext, $pUrl){
		$this->text = $ptext;
		$this->url = $pUrl;
	}
	
	function getText(){
		return $this->text;
	}
	
	function getUrl(){
		return $this->url;
	}
	
		
	function getImageUrl(){
		return $this->imageUrl;
	}
	
	function getTextHTMLlink(){
		$link = "<a href='" . $this->url . "'>" . $this->text . "</a>";
		return $link;
	}
	
}
?>

```

What am I doing wrong?

---

### Post by catchmeifyoutry on 2009-01-02
[PHP]
$this->items[$this->numitems] = new navMenuItem($itemTitle,$itemUrl);
[/PHP]
You write numitems instead of numItems here, maybe you keep assigning new navMenuItem's to key NULL?
Maybe you can put a quick 'n dirty check in toHTMLTable() to see what keys of $this->items are set, e.g.:
[PHP]
function toHTMLTable(){
		// DEBUG
		var_dump(array_keys($this->items));
		$table = "<table><tr><td>" . $this->title . "</td></tr>";
[/PHP]

Some other comments, if you're interested:
It's usually more logical to let a counter such as numItems start at zero, and always reflect the size of the array $this->items. In other words: this->numItems === count($this->items);
I believe you're current approach is due to the way new objects are assigned to items (see line in my comment above). Your approach should only be necessary if you plan to remove items and but add new ones to a unique key. Otherwise, why not use the much simpler (and less error prone)
[PHP]
$this->items[] = new navMenuItem($itemTitle,$itemUrl);
[/PHP]
The for loop would then use just the less than comparison $counter < $this->numItems; But the loop can already be rewritten even simpler:
[PHP]
		foreach($this->numItems as $item)
		{
			$table .= "<tr><td>";
			$table .= $item->getTextHTMLlink();
			$table .= "</td></tr>";

		}
[/PHP]

Hope this helps

---

