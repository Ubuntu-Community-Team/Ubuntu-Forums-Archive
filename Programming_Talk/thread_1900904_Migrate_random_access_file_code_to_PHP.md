---
title: "Migrate random access file code to PHP"
date: 2011-12-27
forum: Programming Talk
---

### Post by wirate on 2011-12-27
```
#include <fstream>
#include <iostream>

using namespace std;

bool find_in_file(char*);
void insert_in_file(char*);
inline bool isNull(char* word);

int main()
{
	char word[25];

	for(int i = 0; i < 10; i++)
	{
		cin >> word;

		if( find_in_file(word) )
			cout << "found" << endl;
		else
			insert_in_file(word);
	}
	system("pause");
}

bool find_in_file(char* word)
{
	ifstream file;
	file.open("file.dat", ios::in);
	char contents[655][25] = {0};
	

	file.read(reinterpret_cast<char*>(contents), 16*1024);
	file.close();

	int i = 0;
	
	while( !isNull(contents[i]) )
	{
		if( strcmp(contents[i], word) == 0)
			return true;

		if( strcmp(contents[i], word) < 0 )
			i = 2*i + 2;
		else
			i = 2*i + 1;
	}

	return false;
}

void insert_in_file(char* word)
{
	fstream file;
	file.open("file.dat", ios::in | ios::binary);
	char contents[655][25] = {0};

	file.read(reinterpret_cast<char*>(contents), 16*1024);
	file.close();


	file.open("file.dat", ios::in | ios::out | ios::binary);

	if( isNull(contents[0]) )
	{
		file.write(word, 25);
		file.close();
		return;
	}

	int parent;
	int current = 0;

	while( !isNull(contents[current]) )
	{
		parent = current;

		if( strcmp( contents[current], word ) < 0 )
			current = current*2 + 2;
		else if ( strcmp( contents[current], word ) > 0)
			current = current*2 + 1;
		else
			return;
	}
	
	int insertAt;

	if( strcmp(contents[parent], word ) < 0 )
		insertAt = parent*2 + 2;
	else
		insertAt = parent*2 + 1;

	file.seekp(insertAt*25, ios_base::beg);
	file.write(reinterpret_cast<const char*>(word), 25);
	file.close();
}

inline bool isNull(char* word)
{
	return word[0] == 0;
}
```

The above code (I am the ashamed author :( )implements a binary search tree on file. It assumes a size of around 16K as max for the file. The tree is stored in this format:

0 root
1 left child of root - L
2 right child of root - R
3 left child of L - LL
4 right child of L - LR
5 left child of R - RL
6 right child of R - RR

and so on. In the absence of a child, an empty node is inserted. Now I have to do the same thing on PHP. How is it possible since as far as I know, PHP does not provide binary file access. Eagerly looking forward to your responses :)

---

### Post by Bachstelze on 2011-12-27
PHP has fopen(), fread(), fwrite() and fclose() functions analogous to their C counterparts, which should do what you want.

[http://www.php.net/manual/en/function.fopen.php](http://www.php.net/manual/en/function.fopen.php)
[http://www.php.net/manual/en/function.fread.php](http://www.php.net/manual/en/function.fread.php)
[http://www.php.net/manual/en/function.fwrite.php](http://www.php.net/manual/en/function.fwrite.php)
[http://www.php.net/manual/en/function.fclose.php](http://www.php.net/manual/en/function.fclose.php)

---

### Post by wirate on 2011-12-27
If I write an integer to file in binary mode, c/c++ will write 4 bytes regardless of the value stored in that integer. PHP will write the plain integer value in file, that is, 0 if the value is 0 and 100 if it is 100. This raises problems when using seek because I dont know the specific number of bytes to move the put pointer. Or in this case, I am writing character arrays of fixed length = 25. How can I do this in php since the variables dont have a type at all?

---

### Post by dazman19 on 2011-12-28
in php this is a lot easier because you have file_get_contents( will open the file, load it into a variable and then close the systems file pointer. 

[PHP]
<?php 

$contents = file_get_contents('blah.pdf');

//in this case $contents could be binary, or ascii text or anything. I can open blah.pdf if i want to, and write a copy to something else. 

file_put_contents('somethingelse.pdf', $contents);

?>

[/PHP]
The problem you have here is performing the binary search. 
your C++ code assumes lines are only 25 characters long. 25x8 in binary, 200 1's and 0's and you would looks for characters by searching through until you hit the EOL character.

So it may be safe to assume as your end of line characters you could explode all the lines into an array. 

<?php
$delimiter = '\n'; // but this could be different depending what the files uses to terminate the lines. 

$contentInLines = explode( $delimiter, $content);


?>

You can use strpos to search each of the items in the array, and if they are found return true and if not return false. 

But i dont know about binary content, you could potentially have problems if your content does not fit in properly. or the EOL characters of the files are different or out of place. I have not done an awful lot of work with manipulating binary, i generally need to understand the format or binary patterns to look for to determine how it is set up.

in answer to your second question i suggest you look at pack() [http://www.php.net/manual/en/function.pack.php](http://www.php.net/manual/en/function.pack.php)

---

