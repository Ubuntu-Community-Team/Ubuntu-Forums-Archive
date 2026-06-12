---
title: "Beginner's Programming Challenge 18"
date: 2011-01-18
forum: Programming Talk
---

### Post by roccivic on 2011-01-18
Hi all, as I am the winner of [Beginner's Programming Challenge 17]("http://ubuntuforums.org/showthread.php?t=1621932") I have the honour of bringing to you Beginner's Programming Challenge 18.

This time the challenge involves some basic cryptography. You must implement the Vigenère cipher in a programming language of your choice. Your program must prompt the user for a plaintext (the message) and a key (the password) and it should output the corresponding cyphertext (the encrypted message). For the sake of simplicity both the message and the key must contain only uppercase letters of the English alphabet.

For bonus points your program should also be able to decrypt a message given a cyphertext and a key.

This is a beginner's challenge, so the source code shouldn't be hard to read. Also please include plenty of comments.

Some reading:
[http://en.wikipedia.org/wiki/Caesar_cipher](http://en.wikipedia.org/wiki/Caesar_cipher)
[http://en.wikipedia.org/wiki/Vigen%C3%A8re_cipher](http://en.wikipedia.org/wiki/Vigen%C3%A8re_cipher)

Best of luck to all.

Rouslan

---

### Post by schauerlich on 2011-01-18
Haskell:
```
import Data.Char
import System(getArgs)

data Crypt = Encrypt | Decrypt deriving (Eq)

-- Takes two characters, one from the original string
-- and one from the corresponding index of the key string.
-- Returns the encrypted (or decrypted) character.
vigenere :: Crypt -> Char -> Char -> Char
vigenere e old key = chr $ 65 + ((p_i `f` k_i) `mod` 26)
  where p_i = (ord old) - 65
        k_i = (ord key) - 65
        f   = if e == Encrypt then (+) else (-)
        
-- Expects 3 command line arguments, the password, the key
-- and an 'e' or 'd' if you want to encrypt or decrypt
-- respectively. The password will be cycled as necessary
-- to be the same length as the source text
main = do
  args <- getArgs
  let [source, pass, x] = take 3 args 
      password = take (length source) (cycle pass)
      e = case (head x) of
               'e' -> Encrypt
               'd' -> Decrypt
    in putStrLn $ zipWith (vigenere e) source password 

```

Here's a similar approach in Python, whited out for the time being:

```
[COLOR="White"]import sys
import operator
from itertools import cycle, islice

def vigenere(f, old, key):
    p_i = ord(old) - 65
    k_i = ord(key) - 65

    return chr(65 + (f(p_i, k_i) % 26))

def main():
    [source, passw, x] = sys.argv[1:4]
    password = list(islice(cycle(passw), 0, len(source)))
    if x == "e":
        f = operator.add
    elif x == "d":
        f = operator.sub

    s = ""
    for i in xrange(len(source)):
        s += vigenere(f, source[i], password[i])

    print s

main()
[/COLOR]
```

---

### Post by unknownPoster on 2011-01-18
> **schauerlich said:**
> ```
import Data.Char
import System(getArgs)

-- Takes two characters, one from the original string
-- and the corresponding character of the key string.
-- To encrypt, f should be (+); to decrypt, (-)
vigenere :: (Int -> Int -> Int) -> Char -> Char -> Char
vigenere f old key = chr $ 65 + ((f p_i k_i) `mod` 26)
  where p_i = (ord old) - 65
        k_i = (ord key) - 65

-- Expects 3 command line arguments, the password, the key
-- and an 'e' or 'd' if you want to encrypt or decrypt
-- respectively. The password will be cycled as necessary
-- to be the same length as the source text
main = do
  args <- getArgs
  let [source, pass, x] = take 3 args 
      password = take (length source) (cycle pass)
      f = case (head x) of
               'e' -> (+) 
               'd' -> (-)
    in putStrLn $ zipWith (vigenere f) source password 

```

what language is that?

---

### Post by cgroza on 2011-01-18
It looks like Haskell to me...

---

### Post by cgroza on 2011-01-18
Just wanted to get rid of a bad number of posts, bump!

---

### Post by bredsaal on 2011-01-18
Python solution.
```
import string,sys

letters = string.uppercase

def vigenere(p,k,d):
	if d:
		i = ( ord(p) - ord(k) - 130) % len(letters)
	else:
		i = ( ord(p) + ord(k) - 130) % len(letters)
	return letters[i]

if len(sys.argv)<4:
	print "Usage:",sys.argv[0],"[plaintext|ciphertext] key [encrypt|decrypt]"
	print "Example:",sys.argv[0]," attackatdawn lemon encrypt"
	sys.exit(1)

text = sys.argv[1].upper()
key = sys.argv[2].upper()

decrypt = False

if sys.argv[3]=='decrypt':
	decrypt = True

c=0
result = ''
for t in text:
	result = result + vigenere(t,key[c % len(key)],decrypt)
	c = c + 1

print result

```

---

### Post by KdotJ on 2011-01-18
Here my shot at it in Java, I decided to implement it by actually creating the cypher table and looking up the characters.

```

public class Cypher {
    
    private static final int ROWS = 26;
    private static final int COLS = 26;
    private static final String alphabet = "ABCDEFGHIJKLMNOPQRSTUVWXYZ";
    private static char[][] table;
    
    //takes 2 args: text, key and 'e' or 'd'
    public static void main(String[] args) {
    	//init the table
    	table = new char[ROWS][COLS];
    	for (int r = 0, offset = 0; r < ROWS; r++, offset++) {
    	    for (int c = 0, pos = offset; c < COLS; c++, pos++) {
    		if (pos == alphabet.length()) {
    	            pos = 0;
    		}
    		table[r][c] = alphabet.charAt(pos);
    	    }
    	}  	
        //Make string upper case
        args[0] = args[0].toUpperCase();
        args[1] = args[1].toUpperCase();
    	//append key if needed
    	while (args[0].length() > args[1].length()) {
    	    args[1] += args[1];
    	}
    	args[1] = args[1].substring(0, args[0].length()+1);	 
    	//loop through each character and encrypt/decrypt   	
    	int pos = 0;
    	StringBuilder output = new StringBuilder(args[0].length());
    	for (int i = 0; i < args[0].length(); i++) {
    	    if (args[2].equalsIgnoreCase("e")) {
    		output.append(encryptChar(args[0].charAt(i), args[1].charAt(i)));
    	    } else if (args[2].equalsIgnoreCase("d")) {
    		output.append(decryptChar(args[0].charAt(i), args[1].charAt(i)));
    	    }
    	} 
    	System.out.println(output.toString()); //print output
    }
    
    //Encrypt character by looking up in table
    private static char encryptChar(char orig, char key) {
    	int r = 0; 
    	int c = 0;
    	for (; c < COLS; c++) {
    	    if (table[c][0] == orig) {break;}
    	}
    	for (; r < ROWS; r++) {
    	    if (table[0][r] == key) {break;}
    	}
    	return table[r][c];
    }
    
    //Decrypt character by looking up in table
    private static char decryptChar(char crypted, char key) {
    	int r = 0;
    	for (; r < ROWS; r++) {
    	    if (table[0][r] == key) {break;}
    	}
    	int c = 0;
    	for (; c < COLS; c++) {
    	    if (table[c][r] == crypted) {break;}
    	}
    	return table[0][c];
    }
}

```

---

### Post by schauerlich on 2011-01-18
> **unknownPoster said:**
> what language is that?

Haskell.

---

### Post by schauerlich on 2011-01-23
Bump, since there are hardly any entries.

---

### Post by Queue29 on 2011-01-23
> **schauerlich said:**
> Bump, since there are hardly any entries.

This was posted the same week university started back up for me, maybe others are busy as well?

Here's an encrypter in Go. I'll add the decrypter tomorrow if I have time. 

```
// UFBPC 18
// @TAGS { UFBPC }
package main

import "fmt"
import "bufio"
import "os"

func main() {
    bufin := bufio.NewReader(os.Stdin)
    
    fmt.Printf("Enter Message: ")
    mess,_ := bufin.ReadString('\n')
    mess = mess[0:len(mess)-1] // trim off newline
    
    fmt.Printf("Enter Key: ")
    key,_ := bufin.ReadString('\n')
    key = key[0:len(key)-1] 
    
    enc := ""
    for i:=0; i<len(mess); i++ {
        enc += vig(mess[i], key[0])
        key = cycle(key)
    }
    
    fmt.Printf("Encrypted: %s\n", enc)
}

func cycle(in string) string {
    ret := in[1:]
    ret += in[0:1];
    return ret
}

func vig( m, k uint8 ) string {
    p_i := m - 65
    k_i := k - 65
    u_i := (65 + (p_i + k_i) % 26)
    return string(u_i);
}
```

Instructions for getting a Go compiler going: [http://golang.org/doc/install.html](http://golang.org/doc/install.html)
Not as easy as something pre-packaged but it's pretty straight forward none the less.

---

### Post by sharpdust on 2011-01-24
Correct me if I'm wrong, but is this not an exact duplicate of a previous challenge?
See: [http://ubuntuforums.org/showthread.php?t=772016](http://ubuntuforums.org/showthread.php?t=772016)

---

### Post by Queue29 on 2011-01-24
> **sharpdust said:**
> Correct me if I'm wrong, but is this not an exact duplicate of a previous challenge?
See: [http://ubuntuforums.org/showthread.php?t=772016](http://ubuntuforums.org/showthread.php?t=772016)

So much more activity back then. What happened to budding linux programmers? :(

---

### Post by roccivic on 2011-01-24
> **sharpdust said:**
> Correct me if I'm wrong, but is this not an exact duplicate of a previous challenge?
See: [http://ubuntuforums.org/showthread.php?t=772016](http://ubuntuforums.org/showthread.php?t=772016)

I had no idea, lol!

---

### Post by krazyd on 2011-01-25
My entry in ruby **1.9.x**.
Features:[LIST]
[*]prompts (as specified in the task! ;))
[*]simultaneous encoding and decoding (accepts a ciphertext or plaintext message)
[*]no hard-coded 'magic numbers'
[/LIST]
```
#!/usr/bin/env ruby

alphabet_length = 'Z'.ord - 'A'.ord + 1
ciphertext = ""
plaintext = ""

print "Enter message: "
message = gets.chomp
print "Enter key: "
key = gets.chomp

# generate the key. it's not truncated to the message length.
key = key * (message.size/key.size + 1)

# split the message into an array of single-character strings, then iterate the
# message array and key simultaneously, (en|de)coding as we go.
message.split(//).each_with_index do |c,i|

  if (encoded_byte = c.ord + key.getbyte(i) - 'A'.ord) > 'Z'.ord
    encoded_byte -= alphabet_length
  end
  ciphertext << encoded_byte

  if (decoded_byte = c.ord - key.getbyte(i) + 'A'.ord) < 'A'.ord
    decoded_byte += alphabet_length
  end
  plaintext << decoded_byte
end

puts "Encoding: #{ciphertext}"
puts "Decoding: #{plaintext}"
```
Usage example:
```
$ ./vig.rb 
Enter message: ATTACKATDAWN
Enter key: LEMON
Encoding: LXFOPVEFRNHR
Decoding: PPHMPZWHPNLJ
$ ./vig.rb 
Enter message: LXFOPVEFRNHR
Enter key: LEMON
Encoding: WBRCCGIRFASV
Decoding: ATTACKATDAWN
$
```

---

### Post by red_Marvin on 2011-01-26
Entering in the obscure languages division: gforth!
you can run it with *$ gforth vignere.fs* (assuming you call the code file vignere.fs)
```
\ longest message we accept
: buf-size 1024 chars ;

\ reads a line from input into a string
\ allocating a buffer for maxlen chars
\ and resizes the string afterwards
: read-string ( maxlen | "name" -- )
create
    dup chars allocate ( maxlen addr wior )
    if ." memory allocation failure" 1 throw then
    dup rot ( addr addr maxlen )
    accept swap over ( newsize addr newsize )
    chars resize ( newaddr newsize wior )
    if ." memory resize failure" 2 throw then
    , ,
does>
    dup @ swap cell+ @
;

\ creates a keyword that each time when activated returns the next
\ character in the string, restarting at the first character after
\ rearching the end
: mk-stringiterator ( addr len / "name" -- )
create
    1- 0 ( addr length offset )
    , , ,
    ( map of varsis [ offset, length, addr ] - so base addr is vars )
does>
    >r ( r:base )

    r@ @ chars ( char-offset )
    r@ 2 cells + @  ( char-offset char-addr )
    + c@ ( key-char )

    r@ dup @ swap 1 cells + @ over ( key-char offset length offset )
    > if 1+ else drop 0 then  ( key-char newoffset )
    r> ! ( key-char )
;

\ converts a charecter to upercase
\ bluntly assuming that it is a letter
: to-uppercase
    dup 96 > 32 * +
;

: encrypt ( msg-xt key-xt len -- addr )
    dup chars allocate ( msg-xt key-xt len addr wior )
    if ." memory allocation failure" 1 throw then
    ( msg-xt key-xt len addr )
    swap 0 do ( msg-xt key-xt addr )
        -rot dup execute to-uppercase 65 - ( addr msg-xt key-xt keych )
        rot dup execute to-uppercase 65 - ( addr key-xt keych msg-xt msgch )
        rot + 26 mod 65 + ( addr key-xt msg-xt resch )
        2swap -rot dup ( msg-xt key-xt resch addr addr )
        i chars + ( msg-xt key-xt resh addr next-addr )
        rot swap ! ( msg-xt key-xt addr )
    loop
    nip nip
;
       

cr ." Please enter the key and press enter: " cr
buf-size read-string encryptionkey
cr ." Please enter the message and press enter: " cr
buf-size read-string message

encryptionkey mk-stringiterator keykey
message mk-stringiterator msgkey

' msgkey ' keykey message nip encrypt
dup message nip
cr cr ." The encrypted message is" cr cr ." <" type ." >" cr cr

encryptionkey drop message drop
free free free

bye
```

---

### Post by red_Marvin on 2011-01-26
Another one, this one in perl, a golfed (readability sacrificed for terseness)
one, but for clarity's sake I've made one that works the same way, but is
expanded and with comments.

Short; the actual cipher substitution happens on line 9 only.
```
#!/usr/bin/env perl
use warnings;
use strict;
print "Enter key please:\n";
my @k = split '', <>;
print "Enter message please:\n";
my @m = split '', <>;
print "Result:\n";
print chr(((ord($m[$_])+ord($k[$_%$#k])-130)%26)+65) for 0..$#m-1;
print "\n";
```

Longer version, I haven't actually tested it, but it should work exactly
the same, only that I buffer the first input line in a temporary variable
for clarity.
```
#!/usr/bin/env perl                 # just tell bash that it is a perl program
use warnings;                       # yell if I do something bad
use strict;                         # be less permissive than default
print "Enter key please:\n";        # text output
my $line = <>;                      # define a scalar line, and read one line
                                    # from stdin into it
my @k = split '', $line             # define an array and split $line into
                                    # individual chars and store into it
print "Enter message please:\n";
my @m = split '', <>;               # shorter version of the above
print "Result:\n";


# start a for loop, the loop variable is $_ by default, and it will iterate
# through the values 0 to the index of the last value in @m minus 1:
# if we have the array @a, then $#a will be the index of the last item in @a
# ( we included '\n' when we read from stdin before, but we don't want it in
# the cipher, so for a string 'FOO\n' => ('F', 'O', 'O', '\n') we want to
# get the chars at 0, 1, 2 == 0..$#m-1 !!

for (0..$#m-1) {
print chr(
        (
            (
                ord(        # ord get's the ascii value of a char  
                    $m[$_]) # if we have the array @a $a[4] will get the item at position 4 in @a
                +ord(
                    $k[$_%$#k]) # modulus with length of key, since keylength can be < messagelength
                -130        # same as -65 -65 to make A<->0 B<->1 etc ('A' has 65 as ascii value)
            )       # now we have summed the numerical values of the message char and the right key char
            % 26    # to keep the value from overflowing
        ) +65       # to convert back so that A<->65 B<->66 etc
    );
}
print "\n";
```

---

### Post by AdotB on 2011-02-16
I'm not sure if this is still open, but I went ahead and gave it a try in Ada.  It's not as short as the others, but I hope it is still readable.

```

----------------------------------------------------------------------------
--  Vigenère Cypher
--
--  compile with:
--    gnatmake -gnat05 vigenere.adb
--
--------------------------------------------------------------------------

with Ada.Text_IO;                   use  Ada.Text_IO;
with Ada.Strings.Unbounded;         use  Ada.Strings.Unbounded;
with Ada.Strings.Unbounded.Text_IO; use  Ada.Strings.Unbounded.Text_IO;
with Ada.Command_Line;              use  Ada.Command_Line;
with Ada.Characters.Handling;       use  Ada.Characters.Handling;

--------------
-- Vigenere --
--------------

procedure Vigenere is

   ---------------
   -- Variables --
   ---------------

   Keyword    : Unbounded_String;
   Input_Text : Unbounded_String;
   Decrypt    : Boolean := False;

   ----------------------
   -- Subprogram Specs --
   ----------------------

   function Rotate_Character (
      Msg     : Character;
      Key     : Character;
      Decrypt : Boolean  := False) return Character;

   function Cipher return Unbounded_String;

   -------------------------------------------------------------------------

   ---------------------
   -- Rotate_Character--
   ---------------------

   --  Find the encrypted (or decrypted) character from input and keyword
   --  characters.
   --  Encrypts input character unless Decrypt is set to True.

   function Rotate_Character (
      Msg     : Character;
      Key     : Character;
      Decrypt : Boolean  := False) return Character
   is
      Diff : Natural;
   begin
      --  Find the difference between the input and keyword characters.
      if Decrypt then
         Diff := (Character'Pos (Msg) - Character'Pos (Key)) mod 26;
      else
         Diff := (Character'Pos (Msg) + Character'Pos (Key)) mod 26;
      end if;

      --  Apply the difference to get the output character, and append it.
      return (Character'Val (Diff + Character'Pos ('A')));
   end Rotate_Character;

   ------------
   -- Cipher --
   ------------

   --  Encrypts input text unless Decrypt is set to True.

   function Cipher return Unbounded_String is
      Input_S   : constant String := To_String (Input_Text);
      Keyword_S : constant String := To_String (Keyword);
      Output    : Unbounded_String;
      Key_Char  : Character;
   begin

      for i in Input_S'Range loop
         --  Get the keyword character associated with the current input
         --  character. Keyword is repeated when its end is reached.
         Key_Char := Keyword_S (((i - 1) mod Keyword_S'Length) + 1);

         --  Get output character.
         Append (Output, Rotate_Character (Input_S (i), Key_Char, Decrypt));
      end loop;

      return Output;
   end Cipher;

   -------------------------------------------------------------------------

begin

   --  If one or more args are given, the first is used as Decrypt,
   --  otherwise the default is used (encrypt).
   if Argument_Count >= 1 then
      if Argument (1) = "decrypt" or else Argument (1) = "d" then
         Decrypt := True;
      elsif Argument (1) = "encrypt" or else Argument (1) = "e" then
         Decrypt := False;
      else
         Put_Line ("Usage: vigenere [encrypt|decrypt] <keyword> <input>");
         return;
      end if;
   end if;

   --  If a second arg is given, it is used as the keyword.
   --  If not, then the user is prompted for the keyword.
   if Argument_Count >= 2 then
      Keyword := To_Unbounded_String (To_Upper (Argument (2)));
   else
      Put ("Keyword: ");
      Keyword := To_Unbounded_String (To_Upper (Get_Line));
   end if;

   --  All other arguments are used as input text.
   --  If no more are given, then the user is prompted for input.
   --  (Spaces are already removed and are not replaced.)
   if Argument_Count >= 3 then
      for i in Positive range 3 .. Argument_Count loop
         Append (Input_Text, To_Upper (Argument (i)));
      end loop;
   else
      Put ("Input Text: ");
      Input_Text := To_Unbounded_String (To_Upper (Get_Line));
   end if;

   --  Process the text.
   Put_Line (Cipher);

end Vigenere;

```

Here is a shorter version as well. About half the size, but i dont like it as much.
```

----------------------------------------------------------------------------
--
--  Vigenère Cypher  (slightly shorter version)
--
--  compile with:
--    gnatmake -gnat05 vig.adb
--
----------------------------------------------------------------------------

with Ada.Text_IO;             use  Ada.Text_IO;
with Ada.Strings.Unbounded;   use  Ada.Strings.Unbounded;
with Ada.Command_Line;        use  Ada.Command_Line;
with Ada.Characters.Handling; use  Ada.Characters.Handling;

procedure Vig is

   Keyword    : Unbounded_String;
   Input_Text : Unbounded_String;
   Decrypt    : Boolean := False;

   --  Encrypt or decrypt the input text.
   function Cipher return Unbounded_String is
      Input_S   : constant String := To_String (Input_Text);
      Keyword_S : constant String := To_String (Keyword);
      Output    : Unbounded_String;
      Key_Char  : Character;
      Diff      : Natural;
   begin
      for i in Input_S'Range loop
         --  Get the keyword character associated with the current input
         --  character. Keyword is repeated when its end is reached.
         Key_Char   := Keyword_S (((i - 1) mod Keyword_S'Length) + 1);

         --  Find the difference between the input and keyword characters.
         if Decrypt then
            Diff := (
               Character'Pos (Input_S (i)) - Character'Pos (Key_Char)) mod 26;
         else
            Diff := (
               Character'Pos (Input_S (i)) + Character'Pos (Key_Char)) mod 26;
         end if;

         --  Apply the difference to get the output character, and append it.
         Append (Output, Character'Val (Diff + Character'Pos ('A')));
      end loop;

      return Output;
   end Cipher;

begin
   if Argument_Count = 0 then
      Put_Line ("Usage: vig [encrypt|decrypt] <keyword> <input>");
      return;
   end if;

   if Argument (1) = "decrypt" or else Argument (1) = "d" then
      Decrypt := True;
   end if;

   Keyword := To_Unbounded_String (To_Upper (Argument (2)));

   for i in Positive range 3 .. Argument_Count loop
      Append (Input_Text, To_Upper (Argument (i)));
   end loop;

   Put_Line (To_String (Cipher));
end Vig;

```

---

### Post by StephenF on 2011-02-16
> **Queue29 said:**
> So much more activity back then. What happened to budding linux programmers? :(
Just a guess but I would say busy writing phone apps.

---

### Post by bioShark on 2011-02-19
Here is my Java solution.

I have also made a small UI in Swing

Main Cipher class:
```
public class Cipher {

	private String plainText;
	private String key;
	private char[][] vigenereTable;

	private static final int rows = 26;
	private static final int columns = 26;
	private static final String alphabet = "ABCDEFGHIJKLMNOPQRSTUVWXYZ";

	/*
	 * Constructor: initializes the Vigenere table and fills it
	 */
	public Cipher() {
		this.vigenereTable = new char[rows][columns];
		createVigenereTable();
	}

	/*
	 * Creating the Vigenere Table
	 */
	public void createVigenereTable() {
		int currentPos = 0;
		for (int i = 0; i < rows; i++) {
			for (int j = 0; j < columns; j++) {
				currentPos = i + j;
				if (currentPos >= alphabet.length()) {
					currentPos = (-1) * (rows - (i + j));
				}
				vigenereTable[i][j] = alphabet.charAt(currentPos);
			}
		}
	}

	/*
	 * Returns the line for the given character
	 */
	private int getLineForChar(String character) {
		for (int i = 0; i < rows; i++) {
			if (Character.toString(vigenereTable[i][0]).equals(character))
				return i;
		}
		return 0;
	}

	/*
	 * Returns the columns for the given character
	 */
	private int getColForChar(String character) {
		for (int i = 0; i < columns; i++) {
			if (Character.toString(vigenereTable[0][i]).equals(character))
				return i;
		}
		return 0;
	}

	/*
	 * Normalize the key
	 */
	public void normalizeTheKey(String plainText, String key) {
		// repeate the key until it matches the length of the plainText
		while (plainText.length() > key.length()) {
			key += key;
		}
		setKey(key.substring(0, plainText.length()).toUpperCase());
		setPlainText(plainText);
	}

	/*
	 * Encripts the plainText parameter with the key, using the vigenereTable
	 */
	public String encrypt(String plainText, String key) {
		String currentChar;
		String encodedResult = "";
		// loop through the plainText characters to encode them
		for (int i = 0; i < plainText.length(); i++) {
			currentChar = Character.toString(plainText.charAt(i)).toUpperCase();
			encodedResult += vigenereTable[getLineForChar(currentChar)][getColForChar(Character
					.toString(key.charAt(i)))];
		}
		return encodedResult;
	}

	public String decrypt(String encyiptedText, String key) {
		String currentChar, currentKey;
		String decryptedResult = "";
		char decriptedChar = 'a';
		// loop through the plainText characters to encode them
		for (int i = 0; i < encyiptedText.length(); i++) {
			currentChar = Character.toString(encyiptedText.charAt(i))
					.toUpperCase();
			currentKey = Character.toString(key.charAt(i));
			// loop through the line of the encripted key
			for (int j = 0; j < columns; j++) {
				if (currentChar
						.equals(Character
								.toString(vigenereTable[getLineForChar(currentKey)][j]))) {
					decriptedChar = vigenereTable[0][j];
				}
			}
			decryptedResult += Character.toString(decriptedChar);
		}
		return decryptedResult;
	}

	public String getPlainText() {
		return plainText;
	}

	public void setPlainText(String plainText) {
		this.plainText = plainText;
	}

	public String getKey() {
		return key;
	}

	public void setKey(String key) {
		this.key = key;
	}
}

```

Here is the Swing dialog

```
import java.awt.Container;
import java.awt.Dimension;
import java.awt.GridBagConstraints;
import java.awt.GridBagLayout;
import java.awt.Insets;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;

import javax.swing.JButton;
import javax.swing.JComboBox;
import javax.swing.JDialog;
import javax.swing.JLabel;
import javax.swing.JTextField;

public class VigenereUI extends JDialog {

	private static final long serialVersionUID = 1L;
	private Cipher cipher = new Cipher();
	private GridBagLayout controlLayout = new GridBagLayout();
	private JButton jBExit = new JButton("Exit");
	private JButton jBGenerate = new JButton("Generate");
	private JComboBox jCBCipherOption = new JComboBox();
	private JTextField jTWorkingText = new JTextField(20);
	private JTextField jTKeyText = new JTextField(20);
	private JLabel jLResult = new JLabel();
	private JLabel jLCipherTypeText = new JLabel("Text to encrypt");

	public VigenereUI() {
		super();
		setTitle("Vigenère cipher");
		setResizable(false);
		fillCipherOptions();
		jCBCipherOption.setPreferredSize(new Dimension(120, 20));
		jBGenerate.setPreferredSize(new Dimension(100, 26));
		jBExit.setPreferredSize(new Dimension(100, 26));
		addComponentsToPane(getContentPane());

	}

	public void addComponentsToPane(final Container pane) {
		pane.setLayout(controlLayout);
		GridBagConstraints c = new GridBagConstraints();

		c.weightx = 0.0;
		c.gridwidth = 2;

		c.gridx = 0;
		c.gridy = 0;
		c.insets = new Insets(10, 10, 10, 10);
		pane.add(new JLabel("Cipher Type"), c);

		c.gridx = 2;
		c.gridy = 0;
		pane.add(jCBCipherOption, c);

		c.gridx = 0;
		c.gridy = 1;
		c.insets = new Insets(10, 10, 10, 10);
		pane.add(jLCipherTypeText, c);

		c.gridx = 2;
		c.gridy = 1;
		pane.add(jTWorkingText, c);

		c.gridx = 0;
		c.gridy = 2;
		c.insets = new Insets(10, 10, 10, 10);
		pane.add(new JLabel("Key"), c);

		c.gridx = 2;
		c.gridy = 2;
		pane.add(jTKeyText, c);

		c.gridx = 0;
		c.gridy = 3;
		pane.add(new JLabel("Result"), c);

		c.gridx = 2;
		c.gridy = 3;
		pane.add(jLResult, c);

		c.gridx = 0;
		c.gridy = 4;
		pane.add(jBGenerate, c);

		c.gridx = 2;
		c.gridy = 4;
		pane.add(jBExit, c);

		jBExit.addActionListener(new ActionListener() {
			public void actionPerformed(ActionEvent e) {
				dispose();
			}
		});
		jCBCipherOption.addActionListener(new ActionListener() {
			public void actionPerformed(ActionEvent e) {
				if (jCBCipherOption.getSelectedItem().equals("Encrypt")) {
						jLCipherTypeText.setText("Text to encrypt");
				} else {
					jLCipherTypeText.setText("Text to decrypt");
				}
			}
		});
		jBGenerate.addActionListener(new ActionListener() {
			public void actionPerformed(ActionEvent e) {
				if (jCBCipherOption.getSelectedItem().equals("Encrypt")) {
					cipher.normalizeTheKey(jTWorkingText.getText(),
							jTKeyText.getText());
					jLResult.setText(cipher.encrypt(cipher.getPlainText(),
							cipher.getKey()));
				} else {
					cipher.normalizeTheKey(jTWorkingText.getText(),
							jTKeyText.getText());
					jLResult.setText(cipher.decrypt(cipher.getPlainText(),
							cipher.getKey()));
				}
			}
		});

		pack();
		setVisible(true);

	}

	public void fillCipherOptions() {
		jCBCipherOption.addItem("Encrypt");
		jCBCipherOption.addItem("Decrypt");
	}

	public static void main(String args[]) {
		java.awt.EventQueue.invokeLater(new Runnable() {
			public void run() {
				VigenereUI dialog = new VigenereUI();
				dialog.addWindowListener(new java.awt.event.WindowAdapter() {
					public void windowClosing(java.awt.event.WindowEvent e) {
						System.exit(0);
					}
				});
				dialog.setVisible(true);
			}
		});
	}
}

```

I have also attached a few screenshots

---

### Post by Bodsda on 2011-02-21
@roccivic
 
Any idea when this will be judged?
If you need any assistance from the beginners team, please send me a PM or drop into #ubuntu-beginners on irc and speak to any voiced user.
 
Thanks,
Bodsda

---

### Post by ja660k on 2011-02-23
Lucky i remembered this was in my bookmarks!

well I needed a refresh in C, so here's mine
(if i can be bothered i will make it compile with -ansi -Wall -pedantic)

[PHP]
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

// prototypes
int encypt(char *input, char *key);
int decrypt(char *EncString, char *key);
int getString(char *string, unsigned length, char *prompt);
void usage();
// end

#define FAILURE 0
#define SUCCESS 1

#define INPUT_LENGTH 20
#define PROMPT_LENGTH 30

#define ENCRYPT 100
#define DECRYPT 200

int main(int argc, char **argv) {
    
    char input[INPUT_LENGTH];
    char key[INPUT_LENGTH];
    char prompt[PROMPT_LENGTH];
    int option = 0;
    
    if(argc == 2) {
        if(strcmp("encrypt",argv[1]) == 0) option = ENCRYPT;
        else if(strcmp("decrypt",argv[1]) == 0) option = DECRYPT;
        else { usage(); return EXIT_FAILURE; }
    }else{ 
        usage();
        return EXIT_FAILURE;
    }
    
    sprintf(prompt,"Enter text :", PROMPT_LENGTH);
    getString(input, INPUT_LENGTH, prompt);

    sprintf(prompt,"Enter Key :", PROMPT_LENGTH);
    getString(key, INPUT_LENGTH, prompt);
    printf("\n");
     
   switch(option){
        case ENCRYPT: encrypt(input,key); break;
        case DECRYPT: decrypt(input,key); break;
    }
    return EXIT_SUCCESS;
}

int encrypt(char *input, char *key) {
    
    int i = 0, keyOffset = 0;
    char p = '\0';

    for(; i < strlen(input); i++){
        if(isalpha(input[i]) && isalpha(key[keyOffset])) {
            //p = (c + k) % 26
            p = ((input[i] - 'A') + (key[keyOffset] - 'A')) % 26;
            p += 'A';
        }else p = input[i];
        
        // print char as it comes out
        printf("%c", p);
        if((keyOffset ++) > strlen(key)) keyOffset = 0;
    }
    printf("\n");
    return SUCCESS;    
}
int decrypt(char *encString, char *key){
    
    int i = 0, keyOffset = 0;
    char c = '\0';
    
    for(; i < strlen(encString); i++){
        if(isalpha(encString[i]) && isalpha(key[keyOffset])) {
            //c = (p - k) % 26
            c = ((encString[i] - 'A') - (key[keyOffset] - 'A')) % 26;
            if(c < 0) c += 26;
            c += 'A';
        }else c = encString[i];

        printf("%c", c);
        if((keyOffset ++) > strlen(key)) keyOffset = 0;
    }
    printf("\n");
    return SUCCESS;
}

int getString (char *string, unsigned length, char *prompt){

    char temp[INPUT_LENGTH + 2];    
    printf("%s", prompt);
    fgets(temp, (length + 2), stdin); // add 2 for '\n' and '\0'
    // can do ALL types of input validation here.
    // for this example, didnt worry about...

    temp[strlen(temp) -1] = '\0'; // override \n with \0
    strcpy(string, temp); // make result available to calling function

    return SUCCESS;
}
void usage() {
    printf("Usage, ./a.out <encrypt | decrypt>\n");
}
[/PHP]

```
$gcc main.c
```

Its probably **way** bigger than it has to be, but nevertheless 
:)

---

### Post by GTMoraes on 2011-02-23
Wow, not so beginner programming, eh?

---

### Post by Queue29 on 2011-02-23
> I have also made a small UI in Swing



Niceeee

---

### Post by Bodsda on 2011-03-07
At the request of the OP, the beginners team will be judging this challenge.
Good luck to all who entered.
 
Bodsda

---

### Post by stchman on 2011-03-08
I chose Java.  My version encrypts and decrypts.

[PHP]
/*
 Program to encrypt OR decrypt a word with a Vigenere cipher 
 */

import java.io.*;

// main Class
public class VigenereCipher
{
    public static void main( String[] args )
    {
        // create variable of type VigenereCipher
        VigenereCipher m = new VigenereCipher();

        // transition to non-static method
        m.getUserInput();
    }
    
    private void getUserInput()
    {
        BufferedReader in = new BufferedReader( new InputStreamReader( System.in ) );

        String choice = new String();
        String word = new String();
        String password = new String();
        String newPassword = new String();
        String cipherText = new String();
        
        System.out.println( "Vigenere Cipher Program\nPlease ONLY use capital letters A-Z\n\n" );
        
        // decide if the user wants to encrypt or decrypt a word
        System.out.print( "Encrypt or Decrypt (E/D)?: " );
        try
        {
           choice = in.readLine(); 
        }
        catch( IOException e ){}
        
        // encrypt choice
        if( choice.charAt( 0 ) == 'e' || choice.charAt( 0 ) == 'E' )
        {
            // get input from user
            System.out.print( "Enter word to be encrypted: " );
            try
            {
                word = in.readLine(); 
            }
            catch( IOException e ){}

            // get cipher key from user
            System.out.print( "Enter password: " );
            try
            {
                password = in.readLine();
            }
            catch( IOException e ){}
            
            // call the createNewPassword method
            newPassword = createNewPassword( word, password );
        
            // call the method to create the encrypted text
            cipherText = encryptCipherText( word, newPassword );
        
            System.out.println( "Encrypted text: " + cipherText );
        }
        
        // decrypt choice
        if( choice.charAt( 0 ) == 'd' || choice.charAt( 0 ) == 'D' )
        {
            // get input from user
            System.out.print( "Enter word to be decrypted: " );
            try
            {
                word = in.readLine(); 
            }
            catch( IOException e ){}

            // get cipher key from user
            System.out.print( "Enter password: " );
            try
            {
                password = in.readLine();
            }
            catch( IOException e ){}
            
            // call the createNewPassword method
            newPassword = createNewPassword( word, password );
        
            // call the method to decrypt the text
            cipherText = decryptCipherText( word, newPassword );
        
            System.out.println( "Decrypted text: " + cipherText );
        }
    }

    // method to create the encoded text from the word and password
    private String createNewPassword( String word, String password )
    {
        // create new password that will be of the same length as the word to be encrypted and repeat
        String newPassword = new String();
        
        // needed ints
        int i = 0;
        int numPasswordLength = 0;
        
        // first must repeat the password to be as long as the word to be encrypted
        // ex:
        // word:         ATTACKATDAWN
        // password:     LEMON
        // new password: LEMONLEMONLE

        // the numPasswordLength will be the number of times the password can divide into the word + the remainder
        numPasswordLength = ( word.length() / password.length() ) * password.length() + ( word.length() % password.length() );

        // create the new password
        if( (int)( word.length() / password.length() ) >= 1 )
        {
            // concatenate the number of time password fits into word
            for( i = 0; i < (int)( word.length() / password.length() ); i++ )
            {
                newPassword += password;
            }

            // concatenate the remainder using modulo arithmetic
            for( i = 0; i < (int)( word.length() % password.length() ); i++ )
            {
                newPassword += password.charAt( i );
            }

        }
        else // the password is longer than the word
        {
            for( i = 0; i < word.length(); i++ )
            {
                newPassword += password.charAt( i );
            }
        }
        
        // return the new password to the calling method
        return newPassword;
    }
    
    private String encryptCipherText( String word, String password )
    {
        // String to contain the cipher
        String cipherText = new String();
        
        // integers
        int i = 0;        
        int result = 0;

        // create the cipher text using the Vigenere algorithm
        for( i = 0; i < word.length(); i++ )
        {
            // use modulo arithmetic to create the cipher, acsii for A is 65, subtract 65 to make zero based
            result = ( ( ( word.codePointAt( i ) - 65 + password.codePointAt( i ) - 65 ) % 26 ) );
            
            // add cipher characters to String, add 65 to go away from 0 reference
            cipherText += Character.toString( (char)( result + 65 ) );
        }
        
        // return the cipher back to the calling method
        return cipherText;
    }

    private String decryptCipherText( String word, String password )
    {
        // String to contain the encrypted text
        String decipherText = new String();
        
        // integers
        int i = 0;        
        int result = 0;

        // create the cipher text using the Vigenere algorithm
        for( i = 0; i < word.length(); i++ )
        {
            // use modulo arithmetic to decipher, acsii for A is 65, subtract 65 to make zero based
            result = ( ( ( ( word.codePointAt( i ) - 65 ) - ( password.codePointAt( i ) - 65 ) ) % 26 ) );

            // check to see if result is negative, if yes add 26
            if( result < 0 )
            {
                // add cipher characters to String, add 65 to go away from zero reference
                // add an additional 26 to alleviate negative number
                decipherText += Character.toString( (char)( result + 65 + 26 ) );
            }
            else
            {
                // add cipher characters to String, add 65 to go away from zero reference
                decipherText += Character.toString( (char)( result + 65 ) );
            }
        }
        
        // return the cipher back to the calling method
        return decipherText;
    }
}
[/PHP]Code for compiling
```
javac -cp . VigenereCipher.java
```

---

### Post by bioShark on 2011-03-18
Does anybody ever judge this contest?

---

### Post by cgroza on 2011-03-19
Don't bother with this thread, no one is even visiting it!

---

### Post by stchman on 2011-03-20
Has a winner even been determined?

---

### Post by roccivic on 2011-03-21
I'm supposed to be judging this, but I forgot about it. I'll try go through the entries ASAP.

---

### Post by bioShark on 2011-03-21
finally :)

Hope you can judge fast :P

---

### Post by roccivic on 2011-03-23
It was very difficult to pick a winner, as all entries were good.

And the winner is....

... _[red_Marvin]("http://ubuntuforums.org/member.php?u=35160")_ with his entry in PERL.

```
#!/usr/bin/env perl                 # just tell bash that it is a perl program
use warnings;                       # yell if I do something bad
use strict;                         # be less permissive than default
print "Enter key please:\n";        # text output
my $line = <>;                      # define a scalar line, and read one line
                                    # from stdin into it
my @k = split '', $line;             # define an array and split $line into
                                    # individual chars and store into it
print "Enter message please:\n";
my @m = split '', <>;               # shorter version of the above
print "Result:\n";


# start a for loop, the loop variable is $_ by default, and it will iterate
# through the values 0 to the index of the last value in @m minus 1:
# if we have the array @a, then $#a will be the index of the last item in @a
# ( we included '\n' when we read from stdin before, but we don't want it in
# the cipher, so for a string 'FOO\n' => ('F', 'O', 'O', '\n') we want to
# get the chars at 0, 1, 2 == 0..$#m-1 !!

for (0..$#m-1) {
print chr(
        (
            (
                ord(        # ord get's the ascii value of a char  
                    $m[$_]) # if we have the array @a $a[4] will get the item at position 4 in @a
                +ord(
                    $k[$_%$#k]) # modulus with length of key, since keylength can be < messagelength
                -130        # same as -65 -65 to make A<->0 B<->1 etc ('A' has 65 as ascii value)
            )       # now we have summed the numerical values of the message char and the right key char
            % 26    # to keep the value from overflowing
        ) +65       # to convert back so that A<->65 B<->66 etc
    );
}
print "\n";
```

Take care,
Rouslan

---

### Post by red_Marvin on 2011-03-23
Thankyou, I have come up with a new challenge, see link:
[http://ubuntuforums.org/showthread.php?p=10593716#post10593716](http://ubuntuforums.org/showthread.php?p=10593716#post10593716)
I hope it is hard, but not too hard.
Good luck everyone!

---

