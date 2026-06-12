---
title: "I'm having difficulty with PHP File Reading"
date: 2017-04-13
forum: Programming Talk
---

### Post by s3a on 2017-04-13
Hello, everyone. :)

The following PHP code is not only taking long to be processed, but it's printing a bunch of NULLs (278,034 NULLs, specifically).:
```
<?php
	echo "I am searching.";
	
	$myFile = fopen("loginFile.txt", "r");
	
	
	while( !feof() ) { // while the end of line has not been reached
		
		$currentLine = fgets($myFile); // get current line of text file
		
		$tokensOfCurrentLineArray = obtainTokensOfLine();
		
		var_dump($tokensOfCurrentLineArray);
	}

	fclose($myFile);
	
	echo "This was reached.<br>";

	function obtainTokensOfLine( $lineOfText) {
		
		$tokensArray;
		$arrayOfChars = str_split( $lineOfText );
		
		$indexOfLastDelimiter = -1;
		for( $i = 0; $i < $arrayOfChars.length; $i++ ) {
			
			$currentToken = "";
			
			if( $arrayOfChars[$i] == ":" || $i == ($arrayOfChars.length-1) ) {
				
				$indexOfCurrentDelimiter = $i;
				for( $j = indexOfLastDelimiter+1; $j <  $indexOfCurrentDelimiter; $j++ ) {
					
					$currentToken += arrayOfChars[$j];
				}
				
				$tokensArray[] = $currentToken;
				
				$indexOfLastDelimiter = $indexOfCurrentDelimiter;
			}
		}
		
		return $tokensArray;
	}

```

Is that amount of NULLs some kind of stop to an infinite loop, or is there 278,034 instructions being processed that I am not aware of, or what? Also, "This was reached.<br>" is not echoed even once, as far as I can tell.

I have a file called loginFile.txt in the same directory as the directory of this php script, with the following contents:
```
login1:pass1
login2:pass2
login3:pass3
```

It seems that the NULLs are from the var_dump function, but why is the array returned by obtainTokensOfLine filled with that many elements?

Could someone please help me figure out how to get my PHP code to properly process a text file, like the one above?

Any help would be GREATLY appreciated!

---

### Post by spjackson on 2017-04-14
I suggest that you fix these issues first:

1. How do you know that fopen() was successful?
2. You need feof($myfile) not feof().
3. You need obtainTokensOfLine($currentLine) not obtainTokensOfLine().

If that's not sufficient, let us know what you get and I'll look more carefully at obtainTokensOfLine.

---

