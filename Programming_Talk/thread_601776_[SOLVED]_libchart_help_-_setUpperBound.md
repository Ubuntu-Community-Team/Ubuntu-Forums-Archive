---
title: "[SOLVED] libchart help - setUpperBound"
date: 2007-11-03
forum: Programming Talk
---

### Post by alanandhispc on 2007-11-03
Hi,

I was wondering if anyone could have a look at this great charting tool called libchart - [http://naku.dohcrew.com/libchart/pages/introduction/]("http://naku.dohcrew.com/libchart/pages/introduction/")
and if possible give me some advice on how to use a public function called setUpperbound that is defined under Bound.php under the classes\axis folder as i believe it needs to be called within the array when your building the chart, but this goes beyond my knowledge of php. my sig is very apt at the moment.

If possible, i would really appreciate it if you could show how this would be used in one of the demo files within the libchart package.

Im using this charting package for a project i am doing for a school, we need to basically be able to set the height of the chart/plot (not the height of the image) so that the students charted progress looks consistent with previous charts.

I have emailed the developer, but have unfortunately had no reply.

Thank you,

Alan

---

### Post by smartbei on 2007-11-03
Here is what you can do. What this does is set the upper limit of the numbers on the y axis of the chart.
Stick the following code near the end of /classes/view/chart/Chart.php (assuming you are using a vertical bar chart. If not, it should work in the other charts at least. Post if you are using a different kind of graph):
[php]
		/**
		 * Override automatic upper bounds calculation.
		 *
		 * @param integer of maximal upper bound
		 */
		public function setUpper($upper) {
			$this->bound->setUpperBound($upper);
		}
[/php]
That should be in the Chart class.

Then, in your php file that creates the chart, put (right after the $chart = new <whatever>Chart();):
[php]
	$chart->setUpper(20);
[/php]
Replacing 20 with the upperbound you want.

This works quite well on my local machine. 

BTW - libchart is indeed quite nice. Might be useful some day.

EDIT: I changed the place you put the function to chart.php, instead of VerticalBarChart.php, so that it works on all charts.

---

### Post by alanandhispc on 2007-11-04
Hi,

thank you for your reply, i am indeed using the vertical bar chart and your code does seem to be doing something, however, it appears to round the figure up as if setUpper is a point rather than an explicit limit to the y axis.

any thoughts?

also, based on version 1.2, what does this bit of code do in bound.php if it's not accessible? 

```
		/**

		 * Set manually the upper boundary value (overrides the automatic formatting).

		 *

		 * @param double upper boundary value

		 */

		public function setUpperBound($upperBound) {

			$this->upperBound = $upperBound;

		}
```

once again, thank you for your reply.

Alan

---

### Post by smartbei on 2007-11-04
That code is the one I am accessing in mine, as you can see. However, $bound (a Bound class object in the chart class) is protected, meaning it can't be accessed by outside functions and statements.Tthe Bound class is the one with the method you are reffering to, and since it is not available for changing directly, I made a simple helper function.

That is odd, from my tests it seemed that it was a hard limit for the y axis, making the graph itself on the chart continue off of the chart area of the generated image.

I am not at home right now, so I will see what I can do tomorrow. :)

---

### Post by alanandhispc on 2007-11-04
the below is what im using, it seems to only round up by the thousand, so setUpper(4000) is ok, but setUpper(4050) goes to 5000. not that my charts will hit the thousands to begin with, but i want to make sure the capability is there for the hard limit.

```
<?php
	/* Libchart - PHP chart library
	 * Copyright (C) 2005-2007 Jean-Marc Trémeaux (jm.tremeaux at gmail.com)
	 * 
	 * This program is free software: you can redistribute it and/or modify
	 * it under the terms of the GNU General Public License as published by
	 * the Free Software Foundation, either version 3 of the License, or
	 * (at your option) any later version.
	 * 
	 * This program is distributed in the hope that it will be useful,
	 * but WITHOUT ANY WARRANTY; without even the implied warranty of
	 * MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
	 * GNU General Public License for more details.
	 *
	 * You should have received a copy of the GNU General Public License
	 * along with this program.  If not, see <http://www.gnu.org/licenses/>.
	 * 
	 */
	
	/*
	 * Vertical bar chart demonstration
	 *
	 */

	include "../libchart/classes/libchart.php";

	$chart = new VerticalBarChart();
	
	$dataSet = new XYDataSet();

	$dataSet->addPoint(new Point("Jan 2005", 273));
	$dataSet->addPoint(new Point("Feb 2005", 421));
	$dataSet->addPoint(new Point("March 2005", 642));
	$dataSet->addPoint(new Point("April 2005", 800));
	$dataSet->addPoint(new Point("May 2005", 1200));
	$dataSet->addPoint(new Point("June 2005", 1500));
	$dataSet->addPoint(new Point("July 2005", 2600));
	$chart->setDataSet($dataSet);
	$chart->setUpper(4050);
	$chart->setTitle("Monthly usage for www.example.com");
		
	$chart->render("generated/demo1.png");

?>
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml">
<head>
	<title>Libchart vertical bars demonstration</title>
	<meta http-equiv="Content-Type" content="text/html; charset=ISO-8859-15" />
</head>
<body>
	<img alt="Vertical bars chart" src="generated/demo1.png" style="border: 1px solid gray;"/>
</body>
</html>
```

i really appreciate your help, thank you.


Alan

---

### Post by smartbei on 2007-11-04
Ok, I have found the place that does this. It is in classes/view/axis/Axis.php . In the computeBoundaries function. Here is a simple way to fix, though this may not be precisely what you are looking for. In that function, replace the line:
[php]
$this->displayMax = ceil($this->max / $this->tics) * $this->tics;
[/php]
with:
[php]
$this->displayMax = $this->max;     //ceil($this->max / $this->tics) * $this->tics;
[/php]
I left the old code in there just in case... who knows...

Anyway, this works well in that the graph is now hard-limited to exactly that upper boundry, but it does not show a 'tick' mark at that upper boundry - that would be more work :p. If you really need it I might try...

No problem...I am enjoying this quite a bit. :)

---

### Post by alanandhispc on 2007-11-07
Hi,

sorry for not getting back sooner, this works great, thank you.

the scale will always be higher than the value, so having the line missing from the top is just a blip compared to having this over-ride function.

Much appreciated, i can crack on with the report building now.


thanks again,

Alan

---

### Post by smartbei on 2007-11-07
Glad I could help.

Please mark thread as solved.

---

### Post by smita1617 on 2008-02-15
Hi...
I am using libchart in my project and encountered the same problem(my bar shoots off the chart area) as mentioned by Alan. Even after making the changes mentioned, my bars refuse to take off and sit adamant on the x-axis. Will really appreciate any help on how to make my graph work. Could you please post in detail how you guys managed to the graph cracking?
Thanks in advance.
PS: I hav attached the image of the graph....Thanks again...

---

