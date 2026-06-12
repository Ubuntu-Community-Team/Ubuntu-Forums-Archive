---
title: "Decimal to Hexadecimal Confusion"
date: 2007-06-11
forum: Programming Talk
---

### Post by renzokuken on 2007-06-11
hi, i need to send some data over a serial connection in HEX form and i'm having a little trouble understanding it.

_Background_
I'm sending instructions over serial to control an x-y stage. All instructions consist of a group of 6 bytes. The first byte is the unit number which you want the data to be sent to. The second byte is the command number (there are about 40 different commands). **The 3rd, 4th, 5th and 6th byte are data in long integer, byte 2's complement format with the least significant byte transmitted first.**

_Problem_
Ok, so i get how the info works, i understand bytes 1 and 2 perfectly, but i'm confused as to how the "data" (3,4,5 and 6) work.

as an example, if i wanted  unit **one** to "move absolute" (command 20), the first two bytes would be:-

0x01, 0x14

(i understand that 0x14 = 1*16 + 4*1  = 20 etc etc).

Now if i want unit 1 to move absolute a distnace of 257 microsteps, the manual says the hex code would be

0x01, 0x14, **0x01, 0x01, 0x00, 0x00**

I dont get how these last four bytes equal 257........can anyone explain?

thanks

PS. hope this makes sense as well

---

### Post by Stephen Howard on 2007-06-11
> 0x01, 0x01

Your sending 2-bytes for X and 2-bytes for Y.  

Assuming 8 bits per byte, you can make up a large number as follows:

First, convert 257 into a 16-bit binary number:

257 = 256 + 1

Least significant byte (ie the 1):
1   *
2
4
8
16
32
64
128

Most significant byte (ie the 256):
256   *
512
1024
2048
4096
8192
16K
32K

Send the LSB first:

0 0 0 0 0 0 0 1

Send the MSB next:

0 0 0 0 0 0 0 1


You also presumably need to deal with negative numbers (ie the 2s complement specification) - if its negative, just flip the bits and add one.

---

### Post by Stephen Howard on 2007-06-11
> dont get how these last four bytes equal 257

Just to be clear, don't think of the four bytes adding up to 257.  The actual number is made from only two bytes, the other two bytes are just padding to make up a stream size.  There are presumably other commands that might use all four bytes - maybe a command that takes both X & Y coordinates at the same time.

---

### Post by renzokuken on 2007-06-11
thanks Stephen, i think i get it now.

i should point out that X and Y are two different units, and each one can be controlled seperately (unit 1 and unit 2). if the first byte eaquals zero though, both units perform the operation. i think the maximum value for command 20 is about 260000. also, using command 20 means i dont have to deal with negatives, command 21 (move relative) means i would.

i only need 10 numbers in Hex form so im gonna give it a go myself and you tell me if i'm right, thanks

the numbers i need in hex are 

20157
46361
72565
98769
124973
151177
177381
203585
229789
255993

so for example 151177 in hex would be:

151177 / 16   =    9448         remainder     9

9448 / 16     =     590           remainder    8

590 / 16     =      36            remainder      14  ( or E )

36 / 16       =      2            remainder     4

2/16       =        0             remainder      2

so the hex code would be

2 4 E 8 9 ........yeah???????

and i'm guessing in the format i want it would be

0x01, 0x14, **0x**.................

k, i got confused and gave up!!!!

how would i write that as 0x01, 0x14, **0x##, 0x##, 0x##, 0x##**

thanks



EDIT

ok, i'm trying again, would it be
```
0x01, 0x14, **0x24, 0xE8, 0x90, 0x00**
``` ???????????????????????????

---

### Post by renzokuken on 2007-06-11
or would it be

0x01, 0x14, **0x02, 0x4e, 0x89, 0x00**???

i think im more confused as to how they define it .....i'll see if i can find the bit in the manual....

ok, i took a snapshot of the relevant part of the manualto make it clearer

---

### Post by Stephen Howard on 2007-06-11
Its easier to convert straight to binary.

There are a few ways to do the conversion, but this is the most error free:

> If the number is odd, write down a '1', if its even, write down a '0'
Subtract the digit you wrote down from the number, and then divide the number by 2.  Repeat

Here's a worked example for 151177

151177 is odd, so write down 1

[INDENT]1[/INDENT]

Subtract 1 from the number gives 151176, and divide it in half:  151176/2=75588
75588 is even, so write down a 0 to the left of the last digit your wrote down

[INDENT]01[/INDENT]

Subtract 0 from 75588 and divide by 2:  75588 / 2 = 37794.  The number is even, so write down '0'.

[INDENT]001[/INDENT]

Subtract 0 from 37794, and divide by 2 = 18897.  The number is odd, so write down '1'.

[INDENT]1001[/INDENT]

Subtract 1 from 18897, and divide by 2 = 9448.  The number is even, so write down a '0'.

[INDENT]01001[/INDENT]

Subtract 0 from 9448 and divide by 2 = 4724.  The number is even, so write down a '0'

[INDENT]001001[/INDENT]

Subtract 0 from 4724 and divide by 2 = 2362.  The number is even, so write down a '0'

[INDENT]0001001[/INDENT]

Subtract 0 from 2362 and divide by 2 = 1181.  the number is odd, so write down a '1'

[INDENT]10001001[/INDENT]

Subtract 1 from 1181 and divide by 2 = 590.  Even, so write '0'.

[INDENT]010001001[/INDENT]

Subtract 0 from 590, divide by 2=295.  Odd, so write '1'

[INDENT]1010001001[/INDENT]

Subtract 1 from 295 and div by 2 = 147.  Odd, so write '1'

[INDENT]11010001001[/INDENT]

Subtract 1 from 147 and div be 2 = 73.  Odd, so write 1

[INDENT]111010001001[/INDENT]

subtract 1 from 73 and div by 2 = 36.  Even, so write 0

[INDENT]0111010001001[/INDENT]

subtract 0 from 36 and div by 2 = 18.  Even, so write 0

[INDENT]00111010001001[/INDENT]

subtract 0 from 18 and div by 2 = 9.  Odd, so write 1

[INDENT]100111010001001[/INDENT]

Subtract 1 from 9 and div by 2 = 4.  Even, so write 0

[INDENT]0100111010001001[/INDENT]

Subtract 0 from 4 and div by 2 = 2.  Even, so write 0

[INDENT]00100111010001001[/INDENT]

subtract 0 from 2 and div by 2 = 1.  Odd, so write 1

[INDENT]100100111010001001[/INDENT]

Phew!


Next, counting from the right, break it up into 8-bit bytes:

[INDENT]10 01001110 10001001[/INDENT]

---

### Post by Stephen Howard on 2007-06-11
> Next, counting from the right, break it up into 8-bit bytes:

    10 01001110 10001001


Then convert to hex:

the right most four bits add up to 9,

'9'

the next most four bits add up to 8,

[INDENT]'89'   (that's the least significant byte)[/INDENT]

the next four bits add up to 14, which is E in hex,

'E'

the next four bits add up to 4, 

[INDENT]'4E'  (that's the next byte)[/INDENT]

the next four bits add up to 2,

[INDENT]'02'  (that's the third byte)[/INDENT]

0x89  0x4E  0x02  0x00

So send:  0x01 0x14 0x89  0x4E  0x02  0x00

---

### Post by Stephen Howard on 2007-06-11
Or use a calculator!!;)

---

### Post by renzokuken on 2007-06-11
will my equipment understand binary though?

i'd rather keep it as hex.

i found this bit of code (written in C, i also have similar for VB) in a demo sample that came with the stage.........

is there a VB function to automatically convert decimal to hex so i dont have to do it myself?

```

/*------------------------------------------------------------------------
 Procedure:     PSERIAL_Send ID:1
 Purpose:       Write a packet to the serial port
 Input:         Unit
                Command
                Data
 Output:        None
 Errors:        None
------------------------------------------------------------------------*/
void PSERIAL_Send( unsigned char Unit,
                   unsigned char Command,
                   long Data )
{
  TxBuffer[0] = Unit;
  TxBuffer[1] = Command;
  // Position 2 is LSB; Position 5 is MSB
  TxBuffer[2] = (Data & 0x000000FF);
  TxBuffer[3] = ((Data >> 8) & 0x000000FF);
  TxBuffer[4] = ((Data >> 16) & 0x000000FF);
  TxBuffer[5] = ((Data >> 24) & 0x000000FF);

  WriteFile( PortHandle,
             TxBuffer,
             PSERIAL_PACKETSIZE,
             &BytesWritten,
             NULL );
}

```

---

### Post by Stephen Howard on 2007-06-11
PS:  the command 21 example in the manual sends a -1.  That's where the 2's complement process comes in (ie its one way to store negative numbers in binary).  2s complement simply means 'flip the bits and add 1'

---

### Post by Stephen Howard on 2007-06-11
> is there a VB function to automatically convert decimal to hex so i dont have to do it myself?

Most languages have a hex conversion function.  If VB is Visual Basic, then it uses a function like:   String = HEX(integer)

No idea if it does 2s complement though as I've never used VB.

---

### Post by renzokuken on 2007-06-11
here is the VB code they use to convert a decimal input into the 4 bytes. could someone possibly explain it to me? thanks

```

Sub Position_to_bytes(ByVal Position As Double)
		' convert the user input data into 4 data bytes to send
		If (optMicrons.Checked = True) Then
			' convert data from microns to microsteps before sending it
			' position [usteps] = position [um] * 64 [usteps/step] / 6.35 [um/step]
			Position = System.Math.Round(Position * 64 / 6.35, 0)
			' since the position in microsteps must be a whole number while
			' the position in microns is not, there will be an error of up to
			' +/- 0.5 microsteps (.05 um) between the requested value in microns
			' and the actual position the program instructs the unit to move to
		End If
		If Position < 0 Then
			'negative value entered by user
			Position = 4294967296# + Position
		End If
		iCommand(6) = Int(Position / (256# * 256# * 256#))
		Position = Position - 256# * 256# * 256# * iCommand(6)
		iCommand(5) = Int(Position / (256# * 256#))
		Position = Position - 256# * 256# * iCommand(5)
		iCommand(4) = Int(Position / 256#)
		Position = Position - 256# * iCommand(4)
		iCommand(3) = Int(Position)
	End Sub

```

---

### Post by renzokuken on 2007-06-11
> **Stephen Howard said:**
> Then convert to hex:

the right most four bits add up to 9,

'9'

the next most four bits add up to 8,

[INDENT]'89'   (that's the least significant byte)[/INDENT]

the next four bits add up to 14, which is E in hex,

'E'

the next four bits add up to 4, 

[INDENT]'4E'  (that's the next byte)[/INDENT]

the next four bits add up to 2,

[INDENT]'02'  (that's the third byte)[/INDENT]

0x89  0x4E  0x02  0x00

So send:  0x01 0x14 0x89  0x4E  0x02  0x00



thanks stephen, i think thats the answer i was looking for, i also now understand what hex actually is and how it relates to binary.............

thanks guys, i'll let you know how it goes

---

### Post by Stephen Howard on 2007-06-11
```
  // Position 2 is LSB; Position 5 is MSB
  TxBuffer[2] = (Data & 0x000000FF);
  TxBuffer[3] = ((Data >> 8) & 0x000000FF);
  TxBuffer[4] = ((Data >> 16) & 0x000000FF);
  TxBuffer[5] = ((Data >> 24) & 0x000000FF);
```

Note the bitwise anding using FF, or 1111 1111

---

### Post by Stephen Howard on 2007-06-11
Finally, you can use the 'bc' command to do your base conversions:

put it into interactive mode using:
```
bc -i
```

Then set the base in which you want the answers (eg 16=base16=hex). 

```
>obase=16

>10
A
```

There's also an ibase setting for specifying the base of the input values.

---

### Post by renzokuken on 2007-06-11
ok, i'll have a go with another number now i think i have it.......

229789 in binary is

11   1000 0001   1001 1101


1st four bytes add up to 13 (D)

2nd four bytes add up to 9

.....so lsb = 9D

3rd four bytes add up to  1

the 4th four bytes add up to 8

.....so next byte is 81

last bytes add up to 3 

so final hex code would be


0x01, 0x14, **0x9d, 0x81, 0x03, 0x00**     ???????????

---

### Post by nerdzero on 2007-06-11
> **renzokuken said:**
> here is the VB code they use to convert a decimal input into the 4 bytes. could someone possibly explain it to me? thanks

```

Sub Position_to_bytes(ByVal Position As Double)
		' convert the user input data into 4 data bytes to send
		If (optMicrons.Checked = True) Then
			' convert data from microns to microsteps before sending it
			' position [usteps] = position [um] * 64 [usteps/step] / 6.35 [um/step]
			Position = System.Math.Round(Position * 64 / 6.35, 0)
			' since the position in microsteps must be a whole number while
			' the position in microns is not, there will be an error of up to
			' +/- 0.5 microsteps (.05 um) between the requested value in microns
			' and the actual position the program instructs the unit to move to
		End If
		If Position < 0 Then
			'negative value entered by user
			Position = 4294967296# + Position
		End If
		iCommand(6) = Int(Position / (256# * 256# * 256#))
		Position = Position - 256# * 256# * 256# * iCommand(6)
		iCommand(5) = Int(Position / (256# * 256#))
		Position = Position - 256# * 256# * iCommand(5)
		iCommand(4) = Int(Position / 256#)
		Position = Position - 256# * iCommand(4)
		iCommand(3) = Int(Position)
	End Sub

```

Hi renzokuken,  lost you from your other post about using SendKeys.  You got it, 229789 is 3819D in hex.   I'll try to explain how this subroutine works and maybe you can use it in your program then.  Let's assume Position = 151177

```
Sub Position_to_bytes(ByVal Position As Double)
		' convert the user input data into 4 data bytes to send

```
		Let's assume that the checkbox is not checked and so this condition is not entered.
```
		If (optMicrons.Checked = True) Then
			'this condition statement is determining if
			'the value passed was microns or microsteps.
			'it is checking the value of a option button control the form.

			Position = System.Math.Round(Position * 64 / 6.35, 0)
			'after executing this statement, the position is
			'now in microsteps
		End If

```


		Since our Position is greater than 0, this condition will also not be entered.
```

		If Position < 0 Then
			'if the user entered a negative value,
			'this converts it (apparently using one's complement and not two's complement).
			Position = 4294967296# + Position

			'4294967296 is 2^32 (Max value for 4 bytes)
			'So if Position = -1 then the binary for 1 would be
			'00000000 00000000 00000000 00000001
			'and -1 in one's complement would be 
			'11111111 11111111 11111111 11111110
			'which is 4294967295 in unsigned decimal.
		End If

```

                These commands use division to get individual bytes from Position.

```

		iCommand(6) = Int(Position / (256# * 256# * 256#))

```
		
		The 256 comes from the max value of 1 byte.
		To get the highest byte, divide by the max value of 3 bytes (2^8 * 2^8 * 2^8 )
		Which can also be represented as 2^24

		Int returns the integer portion of whatever number you give it.
		It always rounds down.
		So, Int(6.1) = 6,  Int(4.5) = 4,  Int(3.9) = 3, etc.

		If Position = 151177 and 2^24 = 16777216 then
		Int(151177 / 16777216) = Int(0.009) = 0
		So, our first byte is 0		

```

		Position = Position - 256# * 256# * 256# * iCommand(6)

```
		We need to remove the byte we just found from our number before we can get the next byte.This leaves the remainder from the result of our integer dvision in the variable 'Position'.
		Since our first value was 0, we are esentially left with the same number
		Position = 151177 - (2^8 * 2^8 * 2^8 * 0) = 151177

```

		iCommand(5) = Int(Position / (256# * 256#))

```
		Now we are trying to get the next byte, so we only divide by the max value of
		2 bytes (256^16 = 65536).
		Int(151177 / 65536) = Int(2.307) = 2

```

		Position = Position - 256# * 256# * iCommand(5)

```
		Now that we actually got a value greater than 0, you might see where this is going
		Position = 151177 - (2^8 * 2*8 * 2) = 20105

		Two more bytes to go, remember, Position has had the first
		two bytes removed
```

		iCommand(4) = Int(Position / 256#)

```
		Int(20105 / 256) = Int(78.535) = 78

		Remove what we just calculated and we will be left with only one byte 
```

		Position = Position - 256# * iCommand(4)

```
		Position = 20105 - 256 * 78 = 137

		which is our last byte
```

		iCommand(3) = Int(Position)

```
		Int(137) = 137
```

	End Sub

```

	Not clear yet?  Let's look at what we calculated for Position = 151177

	iCommand(6) = 0
	iCommand(5) = 2
	iCommand(4) = 78
	iCommand(3) = 137

	And in hex would be...

	iCommand(6) = 0
	iCommand(5) = 2
	iCommand(4) = 4E
	iCommand(3) = 89

So that's how that subroutine works.  You give a number, it fills the integer array iCommand (which you have to declare at the form-level) with the appropriate bytes.  You just need to set iCommand(2) and iCommand(1) with your instruction codes then.

FYI, If you need the hex representation of a number in VB, You can just use the Hex function as stephen recommended.  In immediate mode (CTRL+G in vb6 not sure what it is in .net) just type

?Hex(151177)

and press ENTER and it will output

24E89 

on the next line.  The Hex function uses two's complement for negative numbers so -1 will return FFFF.

If you need to go the other way, just prefix your hex number with &H

?&H24E89 in immediate mode will output 151177

---

### Post by nerdzero on 2007-06-11
> **Stephen Howard said:**
> ```
  // Position 2 is LSB; Position 5 is MSB
  TxBuffer[2] = (Data & 0x000000FF);
  TxBuffer[3] = ((Data >> 8) & 0x000000FF);
  TxBuffer[4] = ((Data >> 16) & 0x000000FF);
  TxBuffer[5] = ((Data >> 24) & 0x000000FF);
```

Note the bitwise anding using FF, or 1111 1111

Stephen's way is much simpler, the equivalent vb syntax (assuming element 1 and 2 contain your instruction) would be

```

TxBuffer[3] = Data And &HFF
TxBuffer[4] = Int(Data / 256) And &HFF
TxBuffer[5] = Int(Data / 65536) And &HFF
TxBuffer[6] = Int(Data / 16777216) And &HFF

```

Goes to show that C is so much more elegant than VB!

---

### Post by renzokuken on 2007-06-11
Can't thank you enough for your help guys........it makes sense now.

i think i can finally start trying to write my code now..........wish me luck.

---

