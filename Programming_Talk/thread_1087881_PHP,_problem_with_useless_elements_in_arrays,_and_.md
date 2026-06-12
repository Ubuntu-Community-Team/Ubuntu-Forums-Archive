---
title: "PHP, problem with useless elements in arrays, and a regex question"
date: 2009-03-05
forum: Programming Talk
---

### Post by hessiess on 2009-03-05
Just for fun, I have bean developing a simple parser for a LISP like markup language in PHP, which I may integrate into my CMS as the LISP syntax allows for a much cleaner markup representation, i.e:

```

(div :id `id`
  (p `This is a paragraph`)
  (a :url `www.whatever.com` (p  `another paragraph`)))

```

So far my parser is mostly working fine, however the resulting parse tree contains a lot of useless elements like "[0] => 1" and "[0] => 0" and I have absolutely no idea where they are coming from, see the following output for example.

```

Array
(
    [0] => Array
        (
            [type] => a
            [parameters] => Array
                (
                    [0] => 
                )

            [children] => Array
                (
                    [0] => 0
                    [1] => Array
                        (
                            [type] => b
                            [parameters] => Array
                                (
                                    [0] => `This
                                    [1] => is
                                    [2] => a
                                    [3] => string`
                                )

                            [children] => NULL
                            [0] => 1
                        )

                    [2] => Array
                        (
                            [type] => c
                            [parameters] => Array
                                (
                                    [0] => `Anouther
                                    [1] => string`
                                )

                            [children] => NULL
                            [0] => 1
                        )

                    [3] => Array
                        (
                            [type] => d
                            [parameters] => Array
                                (
                                    [0] => `Yet
                                    [1] => anouther
                                    [2] => string`
                                    [3] => 
                                )

                            [children] => Array
                                (
                                    [0] => 0
                                    [1] => Array
                                        (
                                            [type] => e
                                            [parameters] => Array
                                                (
                                                    [0] => `and
                                                    [1] => anouther`
                                                )

                                            [children] => NULL
                                            [0] => 1
                                        )
                                )
                        )
                )
        )

    [1] => Array
        (
            [type] => f
            [parameters] => Array
                (
                    [0] => `and
                    [1] => anouther`
                )

            [children] => NULL
            [0] => 1
        )
)

```

Any ideas where these are comeing from?

This is the complete code for the program, the array creation code is between lines 81 and 101.

[PHP]
<?php
// Test code to parse
    $input_code = "
    (a
      (b `This is a string`)
      (c `Anouther string`)
      (d `Yet anouther string`
        (e `and anouther`)))
      (f `and anouther`)";

// create parser
    $parser = new lisp_parser();
    $parse_tree = $parser -> parse_string($input_code);

// display tree
    print "<pre>";
    print_r($parse_tree); 
    print "</pre>";

///////////////////////////////////////////////////////////////////////////
    class lisp_parser
    {
	public function parse_string($string)
	{
	// tree for storing the result
	    $parse_tree = NULL;

	// parse
	    $parse_tree = $this->extract_s_exp($string, $parse_tree, 0);

	// return
	    return $parse_tree;
	}

///////////////////////////////////////////////////////////////////////////
	private function extract_s_exp($exprsession_string, $tree, $counter)
	{
	    $expressions = str_split($exprsession_string);

	// loop over the input character by character
	    for($i = 0; $i < count($expressions); $i ++)
	    {
		$char = $expressions[$i]; 

		$depth = 1;
		$tot_depth = 0;

	// string for storing the parsed s-expression
		$new_s_exp = "";

	    // find the first opening parantisies
		if($char == '(')
		{
		// find the matching closing parantasies
		    for($chunklen = $i + 1; $chunklen < count($expressions); $chunklen ++)
		    {
			$char = $expressions[$chunklen]; 

			if($char == '(')
			{
			    $depth ++;
			    $tot_depth = $depth;
			}


		    // find closing
			else if($char == ')')
			{
			    $depth --;

			    if($depth == 0)
			    {
				break;
			    }
			}

			$new_s_exp .= $char;

			$i ++;
		    }

		// build tree
		    $paramiters = $this->split_params($this->strip_s_exp($new_s_exp));
		    $type = array_shift($paramiters);

		    if($tree == NULL && $counter == 0)
		    {
			$counter = 1;

			$tree = array(0 => array('type' => $type,
			    'parameters' => $paramiters, 'children' =>
			    $this->extract_s_exp($new_s_exp, $tree[0]['children'], $counter)));
		    }

		    else if($tot_depth > 1)
		    {
			array_push($tree, array('type' => $type,
			    'parameters' => $paramiters, 'children' =>
			    $this->extract_s_exp($new_s_exp, $tree[0]['children'], $counter)));
		    }

		    else
		    {
			if($tree == NULL)
			{
			    $tree = array(0);
			}
			array_push($tree, array('type' => $type,
			    'parameters' => $paramiters, 'children' => "NULL", $counter));
		    }
		}
	    }
	    return $tree;
	}

///////////////////////////////////////////////////////////////////////////
// strip s-expressions from a string
///////////////////////////////////////////////////////////////////////////
    private function strip_s_exp($exprsession_string)
    {
	$expressions = str_split($exprsession_string);
	$depth = 0;

	$new_s_exp = "";
	foreach($expressions as $char)
	{
	    if($char == '(')
		$depth += 1;

	    if($depth == 0)
		$new_s_exp .= $char;

	    if($char == ')')
		$depth -= 1;
	}
	return $new_s_exp;
    }

///////////////////////////////////////////////////////////////////////////
// Separate individual paramiters into an array
///////////////////////////////////////////////////////////////////////////
    private function split_params($s_expres)
    {
	$result = split("[\n\r\t ]+", $s_expres);
	return $result;
    }
}
?>
[/PHP]

Also, how would I go about structuring a regular expression which will break the parameter string into words, but keep anything between back ticks as a single string?

---

### Post by hessiess on 2009-03-07
bump.

---

