---
title: "PHP Loop through arrays within an array"
date: 2008-04-23
forum: Programming Talk
---

### Post by gambrjl on 2008-04-23
Ok, going crosseyed here so I figured you smart folks could point me in the right direction.  I have an array with 4 keys where the value associated with each key is an array (all of those arrays are the same length)

The array looks similar to this with a var_dump()

array(2) {
["Key 1"] => array (3) {
          [0] => string "value1"
          [1] => string "value2"
          [3] => string "value3"
}
{
["Key 2"] => array (3) {
          [0] => string "value4"
          [1] => string "value5"
          [3] => string "value6"
}
}

I'd like the table to look like this

Key 1       Key 2
value1      value4
value2      value5
value3      value6

does that make sense?  I can't figure out how to loop through and get table to come out correct

---

### Post by RainCT on 2008-04-23
There might be a better way (I haven't used PHP for some time now), but this should work:

```

<?PHP

$array = array(
		'Key 1' => array(
				'Value 1',
				'Value 2',
				'Value 3',
			),
		'Key 2' => array(
				'Value 4',
				'Value 5',
				'Value 6',
			),
	);

print '<table width="300px"><tr>';
$num_elements = 0;
foreach($array AS $key => $value) {
	print '<td><b>'.$key.'</b></td>';
	if (count($value) > $num_elements) {
		$num_elements = count($value);
	}
}
print '</tr>';
for($i = 0; $i < $num_elements; $i++) {
	print '<tr>';
	foreach($array AS $value) {
		print '<td>'.$value[$i].'</td>';
	}
	print '</tr>';
}
print '</table>';

?>

```

---

### Post by gambrjl on 2008-04-23
> **RainCT said:**
> There might be a better way (I haven't used PHP for some time now), but this should work:


Thanks RainCT.  I'll will give that a shot and see where it gets me

---

