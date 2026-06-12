---
title: "FILE I/O problems"
date: 2010-11-02
forum: Programming Talk
---

### Post by YourMomsASmurph on 2010-11-02
Im creating a simple substitution cipher program (So that I can test a (non brute force) program that will decipher it w/o the key.)

The problem is that I don't seem to understand input and output. As far as I can tell.. This SHOULD work. I think I'm just missing something simple. 

This code is supposed to start at the beginning of the file, it then looks for characters to place in the character array.

The file includes commented out sections denoted by 
//
and is supposed to ignore white space. '\n' and ' '

I'm not sure whats wrong with it. please let me know if 
[PHP]    int index = 0;
    while(!encryptKey.eof()) {
        cout << index <<"\n";


        encryptKey.get(tempCipherChar);

        /*Find and ignore invalid characters*/

        if (tempCipherChar == '/') { //Ignore commented out sections of text
            encryptKey.get(tempCipherChar);
            if (tempCipherChar == '/') {
                while(tempCipherChar != '\n' ) {
                    encryptKey.get(tempCipherChar); //get new chars until line is done
                }
            }
        }//end if

        while(tempCipherChar == ' ' || tempCipherChar == '\n') { //Ignore white Spacec
            encryptKey.get(tempCipherChar);
        }

        /*Invalid checking ended*/

        cipherChar[index] = tempCipherChar;
        index++;

    }//End while eof

[/PHP]

The program seems to run run the main loop too many times. (There should only be 52 valid characters in the file BUT! the program runs through over 600 times)

---

### Post by Arndt on 2010-11-03
> **YourMomsASmurph said:**
> Im creating a simple substitution cipher program (So that I can test a (non brute force) program that will decipher it w/o the key.)

The problem is that I don't seem to understand input and output. As far as I can tell.. This SHOULD work. I think I'm just missing something simple. 

This code is supposed to start at the beginning of the file, it then looks for characters to place in the character array.

The file includes commented out sections denoted by 
//
and is supposed to ignore white space. '\n' and ' '

I'm not sure whats wrong with it. please let me know if 
[PHP]    int index = 0;
    while(!encryptKey.eof()) {
        cout << index <<"\n";


        encryptKey.get(tempCipherChar);

        /*Find and ignore invalid characters*/

        if (tempCipherChar == '/') { //Ignore commented out sections of text
            encryptKey.get(tempCipherChar);
            if (tempCipherChar == '/') {
                while(tempCipherChar != '\n' ) {
                    encryptKey.get(tempCipherChar); //get new chars until line is done
                }
            }
        }//end if

        while(tempCipherChar == ' ' || tempCipherChar == '\n') { //Ignore white Spacec
            encryptKey.get(tempCipherChar);
        }

        /*Invalid checking ended*/

        cipherChar[index] = tempCipherChar;
        index++;

    }//End while eof

[/PHP]

The program seems to run run the main loop too many times. (There should only be 52 valid characters in the file BUT! the program runs through over 600 times)

Print out tempCipherChar also; then you'll see more of what your program is doing.

52 is so small so I would probably try the debugger directly, and singlestep everything.

---

