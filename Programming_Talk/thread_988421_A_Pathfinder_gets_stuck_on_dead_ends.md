---
title: "A* Pathfinder gets stuck on dead ends"
date: 2008-11-20
forum: Programming Talk
---

### Post by tom66 on 2008-11-20
I have written a pathfinder in PHP. It works great, however, when it comes to a dead-end it gets stuck and never exits. 

[php]
<?php

$area = array(
	// Floor 1; point with '9' is the goal.
	//	    point with '1' is a wall/unavailable area. 
	//	    point with '0' is a coridoor.
	//          point with '2' is an elevator or stairs system.
	//          point with '8' is the start position, e.g. the door of a room.
	//
	// You can have multiple stair systems. All are explored. 
	array(
		array(1, 1, 0, 1, 1, 1, 1, 1),
		array(1, 0, 0, 0, 1, 1, 1, 1),
		array(1, 0, 0, 0, 0, 0, 0, 1),
		array(1, 0, 0, 0, 1, 1, 1, 1),
		array(1, 0, 0, 0, 1, 1, 1, 1),
		array(1, 1, 0, 0, 0, 0, 0, 1),
		array(1, 1, 1, 1, 1, 1, 2, 1),
		array(1, 1, 1, 1, 1, 1, 1, 1),
		array(1, 1, 1, 1, 1, 1, 1, 1),
	),
	array(
		array(1, 8, 1, 1, 1, 1, 1, 1),
		array(1, 0, 0, 0, 0, 0, 0, 0),
		array(1, 1, 1, 0, 1, 1, 0, 1),
		array(1, 1, 1, 0, 1, 1, 0, 1),
		array(1, 1, 1, 0, 1, 1, 0, 1),
		array(1, 1, 1, 0, 1, 1, 0, 1),
		array(1, 1, 1, 0, 1, 1, 2, 1),
		array(1, 1, 1, 1, 1, 1, 1, 1),
		array(1, 1, 1, 1, 1, 1, 1, 1),
	)
);

/**
 * Finds the last occurance of an element on a single floor.
 *
 * @param	floor data array
 * @param	item to find
 *
 * @return	x,y array for the point, returns -1, -1 on failure to find.
 */
function find_last_pos($floor_data, $item)
{
	$point = array(-1, -1);
	
	foreach($floor_data as $y => $y_row)
	{
		foreach($y_row as $x => $x_point)
		{
			if("$x_point" == "$item")
			{
				$point = array($x, $y);
			}
		}
	}
	
	return $point;
}

/**
 * Finds the F-cost of a particular square.
 * 
 * The F-cost is the sum of the distance (H) to the goal,
 * calculated with the Manhattan Method; we take the remaining
 * X and the remaing Y to the goal and add them together. This 
 * is only an estimate, however, and is certainly not the quickest
 * way to get to a particular point.  
 *
 * We don't use any cost for moving (G), as each type of move is
 * considered the same cost. So our F-cost is simply our heuristic. 
 *
 * @param	open list data
 * @param	end x,y array
 *
 * @return	F-cost
 */
function get_f_cost($open_list_node, $end_xy)
{
	$end_x = $end_xy[0];
	$end_y = $end_xy[1];
	
	$h = (abs($end_x - $open_list_node['self'][0]) + abs($end_y - $open_list_node['self'][1]));
	
	return $h;
}

/**
 * Finds an item in the OK list/points array, and returns 
 * it's index. Takes an 'open list' style format only.
 *
 * @param	ok list array
 * @param	open list item
 *
 * @return	index position or -1 on failure
 */
function find_in_ok_list($ok_list, $item)
{
	foreach($ok_list as $point => $ok_list_point)
	{
		if($ok_list_point == $item['self'])
		{
			return $point;
		}
	}
	
	return -1;
}

/**
 * Checks if item exists in the open list. 
 *
 * @param	open list array
 * @param	points x,y
 *
 * @return	returns the position of the item, or returns 
 *		-1 if it can't be found.
 */
function find_in_open_list($open_list, $xy)
{
	foreach($open_list as $point => $open_list_point)
	{
		if(($open_list_point['self'][0] == $xy[0]) &&
		   ($open_list_point['self'][1] == $xy[1]))
		{
			return $point;
		}
	}
	
	return -1;
}

/** 
 * The main pathfinding routine. Finds the route between two points.
 * Works only on one floor. Call per floor using multiple functions
 * to have a fully functioning pathfinder.
 *
 * @param	floor data array
 * @param	start x,y array
 * @param	end x,y array
 *
 * @return	multi-dimensional array of points of the path, or 
 *		an empty array on failure to find a path or general 
 *		error.
 */
function pathfinder_xy($floor_data, $start_xy, $end_xy)
{
	/*
	 * Most of this code is based on the tutorial at:
	 *  http://www.policyalmanac.org/games/aStarTutorial.htm
	 * Thanks to the author!
	 */
	/*
	 * Extract the juicy data from the arrays.
	 */
	$start_x = $start_xy[0];
	$start_y = $start_xy[1];
	
	$end_x = $end_xy[0];
	$end_y = $end_xy[1];
	
	/*
	 * Initial setup.
	 */
	$finished_path = array();
	$ok_points = array();
	$open_list = array();
	$path_found = false;
	
	/*
	 * Populate the 'ok_points' array. This is initially
	 * filled with all walkable points, but we'll drop the
	 * ones we have visited from this array.
	 */
	foreach($floor_data as $y => $y_row)
	{
		foreach($y_row as $x => $x_point)
		{
			if($x_point == 1)
				continue;
			
			$ok_points[] = array($x, $y);
		}
	}
	
	/*
	 * Are our starting and ending points in the OK list? 
	 * If not... that'd be a problem.
	 */
	if(!in_array($start_xy, $ok_points))
		return array();
	if(!in_array($end_xy, $ok_points))
		return array();
	
	/*
	 * Add our starting node to the open list.
	 */
	$open_list[] = array(
			'self'   => array($start_x, $start_y), 	/* this square */
			'parent' => array(-1, -1),		/* the parent, e.g. none at the moment */ 
			'fcost'  => NULL			/* f-cost of square */
		);
	
	$open_list[0]['fcost'] = get_f_cost($open_list[0], $end_xy);
	
	/*
	 * The main loop. It currently has a set limit of 1,000 
	 * iterations to prevent problems in the code from freezing
	 * the server. 
	 */
	for($i = 0; $i < 1000; $i++)
	{
		/*
		 * Stop if we have no more open list nodes. This means 
		 * the path is impossible, there is no solution.
		 */
		if(count($open_list) == 0)
			break;
		 
		/*
		 * Find the lowest F-cost node in the open list.
		 *
		 * The lowest F-cost used initially is the first item in the
		 * open list - this is to prevent against the problem of 
		 * choosing a really big number and hoping it's the lowest,
		 * when it might not be (causing problems). 
		 */
		$f_cost_lowest = get_f_cost($open_list[0], $end_xy);
		$f_cost_lowest_id = 0;
		
		foreach($open_list as $open_list_node_id => $open_list_node)
		{
			$f_cost = get_f_cost($open_list_node, $end_xy);
			
			if($f_cost < $f_cost_lowest)
			{
				echo "While searching for fcost: found low of $f_cost @ $open_list_node_id. <br />";
				
				$f_cost_lowest = $f_cost;
				$f_cost_lowest_id = $open_list_node_id;
			}
		}
		
		/*
		 * Our current square is the lowest F-cost square.
		 * 
		 * First, we remove it from the 'ok_list', to make
		 * sure we don't traverse it. 
		 *
		 * Then we find the neighbours of this current square.
		 */
		$current = $open_list[$f_cost_lowest_id];
		$point_of = find_in_ok_list($ok_points, $current);
		
		if($point_of != -1)
			unset($ok_points[$point_of]);
		
		$n_ok = 0;
		
		for($xp = -1; $xp <= 1; $xp++)
		{
			for($yp = -1; $yp <= 1; $yp++)
			{
				/*
				 * Avoid using diagonals. Could mean false positive.
				 */
				if($xp == -1 && $yp == -1) continue;
				if($xp == -1 && $yp ==  1) continue;
				if($xp ==  1 && $yp == -1) continue;
				if($xp ==  1 && $yp ==  1) continue;
				
				/*
				 * We find the 4 neighbours by going from x -1 .. 1 and
				 * y -1 .. 1. We then using 'xw' and 'yw' as X-working
				 * and Y-working appropriately.
				 */
				$xw = $current['self'][0] + $xp;
				$yw = $current['self'][1] + $yp;
				
				/*
				 * Check if this is an OK square.
				 */
				$point_array = array(
						'self'   => array($xw, $yw),
						'parent' => array(-1, -1),
						'fcost'  => NULL
					);
				
				if(find_in_ok_list($ok_points, $point_array) == -1)
				{
					echo "Point at $xw, $yw was not OK, so ignoring. <br />";
					
					/* Ignore if not OK. */
					continue;
				}
				
				/*
				 * Increment the neighours_ok counter to make sure we don't
				 * trap ourselves in a dead end. 
				 */
				$n_ok++;
				
				/*
				 * Check if this is on the open list. If it isn't:
				 *  - Add it to the open list;
				 *  - Mark the current square the parent of this square.
				 *
				 * Else:
				 *  - Check to see if this square is better. If that is so
				 *    change the parent of the square to the current square.
				 */
				$pos_in_open_list = find_in_open_list($open_list, array($xw, $yw));
				
				if($pos_in_open_list == -1)
				{
					$open_list[] = array(
							'self'   => array($xw, $yw),
							'parent' => $current['self'],
							'fcost'  => NULL
						);
					
					$open_list[count($open_list) - 1]['fcost'] = get_f_cost($open_list[count($open_list) - 1], $end_xy);
					
					echo "Added an item to the open list ($xw, $yw). <br />";
				}
				else
				{
					/*
					 * Check to see if this square is 'better' than the 
					 * current square.
					 */
					echo "Didn't add an item ($xw, $yw) ";
					
					$this_square = $open_list[$pos_in_open_list];
					
					if($this_square['fcost'] < $current_square['fcost'])
					{
						echo "... but fcost was lower so setting parent <br />";
						$this_square['parent'] = $current_square['self'];
					}
					else
					{
						echo "... fcost was higher/equal, so not doing anything with this square<br />";
					}
				}
			}
		}
			
		/*
		 * Stop if we have reached the destination.
		 * This means all the code above wasn't fruitless!
		 */
		$pos_in_open_list = find_in_open_list($open_list, $end_xy);
		
		if($pos_in_open_list != -1)
		{
			$path_found = true;
			echo "Yay, found path!<br />";
			
			break;
		}
	}
	
	/*
	 * If we found the path (yay) trace it back.
	 */
	if($path_found == true)
	{
		$pos_in_open_list = find_in_open_list($open_list, $end_xy);
		
		/*
		 * Follow the parent back. Limit of 2,000 operations 
		 * for this to prevent server problems and the like.
		 */
		$current_parent = $open_list[$pos_in_open_list]['parent'];
		$finished_path[] = $current_parent;
		
		for($k = 0; $k < 2000; $k++)
		{
			echo "Traversing parents... currently on iteration $k, parent is $current_parent[0], $current_parent[1]<br />";
			
			$parent_pos_in_open_list = find_in_open_list($open_list, $current_parent);
			$current_parent = $open_list[$parent_pos_in_open_list]['parent'];
			
			$finished_path[] = $current_parent;
			
			if($current_parent == $start_xy)
			{
				echo "Ending traversal on iteration $k at $current_parent[0], $current_parent[1] which is equal to $start_xy[0], $start_xy[1] (start_xy)<br />";
				break;
			}
		}
	}
	
	/*
	 * We're done. Return the finished path. If this is empty, 
	 * then no path was found.
	 */
	return $finished_path;
}

?>


<h1>Pathfinder Test (A*)</h1>
<p>
	<?php
	
	$path = pathfinder_xy($area[1], find_last_pos($area[1], '8'), find_last_pos($area[1], '2'));

	echo "<table width=\"500\" cellspacing=\"0\" cellpadding=\"0\" style=\"background-color: #666666; \">\n";
	
	foreach($area[1] as $y => $y_row)
	{
		echo "<tr>";
		
		foreach($y_row as $x => $x_item)
		{
			$style = "text-align: center; ";
			
			if(!in_array(array($x, $y), $path))
			{
				if($x_item == 0)
					$style .= "background-color: #999999; color: #000000; ";
				else if($x_item == 1)
					$style .= "background-color: #222222; color: #FFFFFF; ";
				else if($x_item == 2)
					$style .= "background-color: #0000FF; color: #FFFFFF; ";
				else if($x_item == 8)
					$style .= "background-color: #FF0000; color: #000000; ";
				else if($x_item == 9)
					$style .= "background-color: #00FF00; color: #000000; ";
			}
			else
			{
				if($x_item == 0)
					$style .= "background-color: #FFFF00; color: #000000; ";
				else if($x_item == 1)
					$style .= "background-color: #222222; color: #FFFFFF; ";
				else if($x_item == 2)
					$style .= "background-color: #0000FF; color: #FFFFFF; ";
				else if($x_item == 8)
					$style .= "background-color: #FF0000; color: #000000; ";
				else if($x_item == 9)
					$style .= "background-color: #00FF00; color: #000000; ";
			}
			
			echo "<td style=\"$style\" height=\"50\" width=\"50\">($x, $y)</td>";
		}
		
		echo "</tr>";
	}
	
	echo "</table>\n";
	
	?>
</p>


[/php]

Yes it is very big. Thanks for everyone's help.

---

### Post by bobbocanfly on 2008-11-20
Is it just me, or can noone else see a '9' (goal point) in either of those arrays? I imagine that could cause a problem, but I'm not sure.

---

### Post by tom66 on 2008-11-20
Oh yeah. But that's probably not the problem as the program does not yet use multiple floors. If there are no dead ends it works great.

---

### Post by ufis on 2008-11-21
I have not taken the time to read through the code, but I can offer my advice of points I got stuck when I did my first A*.

I followed this A* tutorial: [http://www.policyalmanac.org/games/aStarTutorial.htm]("http://www.policyalmanac.org/games/aStarTutorial.htm")

One reason I can think of that you are getting stuck in dead ends is that you have no way in your code to get back to your open list once you reach a square with no open blocks next to it (i.e. dead end). Once you reach a dead end you need to go back to your open list, looking for the square in the open list with the best score.

If you reach a dead end, and your open list is empty, it means there is no path. If there should be a path, recheck your management of your open list. One mistake I made was to drop some squares from the open list before I used them (due to some bad coding).

---

### Post by ufis on 2008-11-21
double post

---

### Post by tom66 on 2008-11-21
IT WORKS!!

Sorry for using caps, but I've been working on it for the past 2-3 days and it hasn't been working... yet. The problem was the f-cost searching algorithm was finding not-ok squares in the open list. It now ignores them, and this works. Yay!

Thanks for your help.

---

