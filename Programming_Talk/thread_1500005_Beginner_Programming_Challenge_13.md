---
title: "Beginner Programming Challenge 13"
date: 2010-06-02
forum: Programming Talk
---

### Post by texaswriter on 2010-06-02
[SIZE=5]Beginner Programming Challenge #13[/SIZE]

Welcome to the 13th Beginner Programming Challenge! 

Hi fora, as the winner of the last beginner programming challenge, I am pleased to present the next challenge. 

For the next challenge, let's make a simple banking program that will take the following as input: 

transaction_code account_number amount
The transaction codes will be as follows: 
**wd** - withdrawal [money taken out of the account]
**dep** - deposit [money put into the account]
**cred** - not what you think it is: [money taken out of the account] YES: this is a withdrawal
**deb** - not what you think it is: [money put into the account] YES: this is a deposit
**fee** - this is money taken out of the account, but not given to the accountholder. Although basically a withdrawal, this is the only code that allows a withdrawal if it makes the balance less than zero OR if the balance is already less than or equal to zero.  

OK, the program will accept as input in the above-named format and make a record of account numbers and the respective balances. The account can NEVER go negative [from the account-holder's perspective] EXCEPT in the case of a fee. In the event of an "overdraft", the withdrawal/credit will NOT be processed, but  a fee will be assessed. 

Here's the challenging part: NO existing database or existing hashing sequence can be used. [COLOR=Red]**Hint**[/COLOR]:  I would recommend using a hashing technique, but as long as an existing database/MySQL method isn't used, I will allow any implementation. 

To simplify what I mean here: the programmer should make everything here from scratch except the container for the data and/or the method of resizing the array. Or in other words. Some languages have an "insert" or "append" entry for arrays. C has remalloc. These are both acceptable or *anything* comparable. If a sort or search method is used, you must make this from scratch. If there is a list.search... you can't use it. 
[COLOR=Red][B]
EXTRA CREDIT REQUIREMENTS ONLY[/B][/COLOR]: If you want extra credit, make your table with a max number of entries so that your overall array can not be a) resizeable b) greater than xx% greater than the maximum number of entries. At the point that you start using malloc and resize, you would have to sort or redo the whole hash table, which is very inefficient. So, to simplify the task, we'll just set a maximum number of entries at 200. That would make the array's maximum size of 200+200*.xx. Want more credit: find out what the minimal percentage is that still allows an efficient hash search/recall routine. 

Please note: regardless of implementation, it will need to accommodate 200 account numbers. 

I will submit a file that will contain sample entries. The bank program won't "open" the file, but the file will be redirected as the std input. This file may contain any number of entries to facilitate making a decisive choice on speed. To clarify, the speed factor is just to encourage people to be wary of the method they choose in storage/retrieval of the account # & balance. 

Here is how I will be judging the entries: 
**1)** **Readability and appropriate commenting.** Following standard code formatting will make your code more readable. Although I have a tendency to comment quite a bit, if you use strategic commenting, you would be surprised how little commenting can actually be useful
**2) Elegance of design.** While not as obvious, consider how a feature is being implemented to see if there is a better way. 
**3) Overall program speed. **To reward those who do this in a way that maximizes speed. Specifically, use whatever implementation you want, but bear in mind that some methods will mean speed sacrifices.
**4) Robustness of design.** If the program handles all the above-named things without crashing and is able to handle all exceptions this will look very good. 
**5) Extra credit. **

Extra credit section: I will try to make two files, one that has 100% correct entries [as in no invalid transaction codes] and one that has many transaction codes. The format for all the data will be correct and inviolable [you don't have to worry about getting text for the account number or dollar amount of transaction]. The account number will be a number with no leading zeros. It will also be an integer. Assume whole dollar amounts. 

Another extra credit will be to see how small a percentage over the max account numbers you can get while still being able to fulfill the maximum account numbers. Or in other words, it should be possible to fit 200 accounts in a 240 entry table. 

This challenge may seem daunting, but once you figure out your hashing routine, the rest of the challenge will be much easier. 

Good luck 

and p.s. until I get a file uploaded, you can test your program with normal input or make up your own file. 
The file will be 3 items wide, separated with a space, the lines will be terminated normally. 
An example input file would be 

dep 11111 25
wd 11111 22599
wd 11111 -2525

---

### Post by lisati on 2010-06-02
> **texaswriter said:**
> 
transaction_code account_number amount
The transaction codes will be as follows: 
wd - withdrawal [money taken out of the account]
dep - deposit [money put into the account]
[B]cred - not what you think it is: [money taken out of the account]
deb - not what you think it is: [money put into the account][/B]
fee - this is money taken out of the account, but not given to the accountholder. 


Nice touch! I see what you did there..... :)

---

### Post by bunburya on 2010-06-02
>  Here's the challenging part: NO existing database or existing hashing  sequence can be used. I would recommend using a hashing technique, but  as long as an existing database/method isn't used, I will allow any  implementation. To simplify what I mean here: the programmer should make  everything here from scratch. 
I don't quite understand this. So in Python, lists, tuples and dictionaries cannot be used? Or can they?

---

### Post by snova on 2010-06-02
> **bunburya said:**
> I don't quite understand this. So in Python, lists, tuples and dictionaries cannot be used? Or can they?

That would be a ridiculous restriction; more likely it bars the use of things like SQL- e.g. "real" databases.

---

### Post by texaswriter on 2010-06-02
bunburya> thanks!!

lisati> Those have built-in capabilities that break that rule. That said, a list by itself or something similar WOULD be fine as long as you never resize it or use built-in functions/libraries to fulfill the challenges laid out.

snova> that is the correct interpretation.

---

### Post by Bodsda on 2010-06-04
> **texaswriter said:**
> bunburya> thanks!!
 
lisati> Those have built-in capabilities that break that rule. That said, a list by itself or something similar WOULD be fine as long as you never resize it or use built-in functions/libraries to fulfill the challenges laid out.
 
snova> that is the correct interpretation.
 
A list in Python is always resizeable. And does the 'from scratch' bit mean I cant use pickle to write a list to file, which would then mean I have to store it in plain textt and write a parser function?
 
Bodsda

---

### Post by StephenF on 2010-06-04
Better to bar certain languages rather than train people to program "badly" in them IMHO.

Also: [http://dictionary.reference.com/browse/C+Programmer%27s+Disease](http://dictionary.reference.com/browse/C+Programmer%27s+Disease)
> _C Programmer's Disease definition_:
The tendency of the undisciplined C programmer to set arbitrary but supposedly generous static limits on table sizes (defined, if you're lucky, by constants in header files) rather than taking the trouble to do proper dynamic storage allocation. If an application user later needs to put 68 elements into a table of size 50, the afflicted programmer reasons that he or she can easily reset the table size to 68 (or even as much as 70, to allow for future expansion) and recompile. This gives the programmer the comfortable feeling of having made the effort to satisfy the user's (unreasonable) demands, and often affords the user multiple opportunities to explore the marvellous consequences of fandango on core. In severe cases of the disease, the programmer cannot comprehend why each fix of this kind seems only to further disgruntle the user.

@Bodsda: The collections.deque object can be declared fixed size.

---

### Post by soltanis on 2010-06-04
I don't get this either; are cred and deb supposed to tell you how much money you've removed and put into the account respectively, or are they dep and wd synonyms?

---

### Post by Blood Rose on 2010-06-04
IMO, this isn't a beginner challenge anymore .. Good luck to everyone who's taking part of this.

---

### Post by lavinog on 2010-06-04
> **texaswriter said:**
>  At the point that you start using malloc and resize, you would have to sort or redo the whole hash table, which is very inefficient.
Wouldn't using a linked-list address this?

---

### Post by sujoy on 2010-06-05
the restrictions are ridiculous IMO, you are making it a "C" challenge without dynamic allocations and so on and so forth ...

---

### Post by ja660k on 2010-06-05
> **sujoy said:**
> the restrictions are ridiculous IMO, you are making it a "C" challenge without dynamic allocations and so on and so forth ...

i was hoping someone wouldn't mention that because i wanted to,
Yes this is looking like a C challenge +1 @sujoy.

Why should we reinvent the wheel when lists are in basically implemented in most other languages... Languages that suit the challenges parameters.

and yes, i do know how to make a list in C; no i did not think it was useless, because in C there is no other choice, aside from realloc to add space to your array.

---

### Post by dv3500ea on 2010-06-05
I've created a program that does everything specified and also accepts bal to query the balance of an acount and exit to exit. It also logs transactions for each account. log account causes the log for that account to be printed to the terminal. A single transaction can be entered as command line arguments.
Also the limit on the number of accounts is practically infinite. Accounts can also have friendly names such as 'savings_account' and 'current_account' instead of arbitrary numbers. I have not used any arrays in my design, opting to use the filesystem instead.

The program was written in ruby using the geany IDE.

```

#!/usr/bin/env ruby
#
#       challenge13.rb
#       
#       Copyright 2010
#       
#       This program is free software; you can redistribute it and/or modify
#       it under the terms of the GNU General Public License as published by
#       the Free Software Foundation; either version 2 of the License, or
#       (at your option) any later version.
#       
#       This program is distributed in the hope that it will be useful,
#       but WITHOUT ANY WARRANTY; without even the implied warranty of
#       MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
#       GNU General Public License for more details.
#       
#       You should have received a copy of the GNU General Public License
#       along with this program; if not, write to the Free Software
#       Foundation, Inc., 51 Franklin Street, Fifth Floor, Boston,
#       MA 02110-1301, USA.

#as I understand the challenge, the input will be:
#   transaction_type acount_number amount

#I will use the /tmp directory as if it were the program's configuration
#directory as this is only a demonstration
Dir.chdir '/tmp'

require 'time.rb'#using core time library for transaction logs

#function to set the balance of a particular account
def set_balance account_num, amount
	#write balance to the file containing the bank balance
	#for the account (.bank_balance_acountnum)
	puts "setting balance of account #{account_num.to_s} to #{amount.to_s}"
	file_name = '.bank_balance_' + account_num.to_s
	file = File.new file_name, 'w'
	file.puts amount.to_s
	file.close
end

#function returning the balance of a specific account
def get_balance account_num
	#if exists a file containing the bank balance (.bank_balance_acountnum),
	#read the balance from it
	#otherwise assume £0 balance
	#and write £0 to the file
	file_name = '.bank_balance_' + account_num.to_s
	balance = 0
	if File.exists? file_name
		#puts "account found"
		file = File.new file_name, 'r'
		balance = file.read.to_f
		file.close
	else
		puts "account not found\ncreating account"
		set_balance account_num, balance
	end
	return balance
end

#function to change the balance of account account_num 
#by amount amount.
#amount can be negative
def change_balance account_num, amount
	balance = get_balance account_num
	puts "old balance: #{balance.to_s}\nchange: #{amount.to_s}"
	balance += amount
	puts "new balance: #{balance.to_s}"
	set_balance account_num, balance
end

#function to log transactions
def log account_num, transaction, amount
	filename = '.bank_log_' + account_num.to_s
	file = File.new filename, 'a'
	file.puts "#{transaction} #{amount.to_s} #{Time.now.strftime("%d/%m/%Y-%H:%M:%S")}"
	file.close
end

def read_log account_num
	filename = '.bank_log_' + account_num.to_s
	file = File.new filename, 'r'
	txt = file.read
	file.close
	return txt
end

def exit_func #what to do on exit
	exit
end

def main input
	if input =~ /(wd|cred|fee) (.*?) (.*?)\s/#handle withdrawal
		amount = -1 * $3.to_f
		account = $2
		if ((get_balance(account) >= -amount) || $1 == 'fee')
			#if sufficiant balance or transaction is a fee
			change_balance account, amount
			#take the amount from the account
			puts "transaction successful"
			log $2, $1, amount
		else
			#disallow transaction
			warn "insufficent balance, transaction cancelled"
		end
	elsif input =~ /(deb|dep) (.*?) (.*?)\s/#handle deposit
		amount = $3.to_f
		account = $2
		change_balance account, amount#take the amount to the account
		puts "transaction successful"
		log $2, $1, amount
	elsif input =~ /bal (.*)/#output balance of account
		puts get_balance($1).to_s
	elsif input =~ /exit/
		exit_func
	elsif input =~ /log (.*?)\s/
		puts '-' * 35
		puts "|transaction_type amount date/time|"
		puts '-' * 35
		puts read_log $1
		puts '-' * 35
	else
		warn "Invalid input format; must be in form:\n (wd|cred|fee|dep|deb) account_number amount\nor (bal|log) account_number"
	end
end


if ARGV.length > 0 #if arguments provided, use them
	main(ARGV[0].gsub('-', '') + ' ' + ARGV[1..2].join(' ') + "\n")
	exit_func#and exit
end

#read data from stdin

while input = gets
	main input
end

exit_func


```

---

### Post by texaswriter on 2010-06-05
Sorry for the misunderstandings. 

I did not intend to restrict the use of lists or a specific language. Let me clarify: Implement this however way you want, except you can't use MySQL/database functions. You can use list and any of its "built-in" abilities like insert. You can even use a resizeable array. NO, this is not a C challenge.

You CAN implement this anyway you want.

I will update the OP to reflect this more clearly. 

If you want more of a challenge however, you will consider the "hint." If you choose to do it another way, that's fine. It's easier to implement this other ways however as well.

---

### Post by ibuclaw on 2010-06-05
Was bored, and stumbled upon this thread. ;)


Implemented the challenge in D.
```

import std.conv;
import std.ctype;
import std.file;
import std.stdio;

/* Tokens IDs for input lines.
   ACTION is the transaction code.
   ID is the account number.
   AMOUNT is the cash amount */
enum
{
    ACTION,
    ID,
    AMOUNT,
}

/* Utility functions */
/* Replaces split() from std.regexp */
string get_line (string input)
{
    int ptr = 0;
    /* Loop through until new line found */
    while (input[ptr] != '\n')
	++ptr;

    return input[0 .. ptr];
}

string[] split_spaces (string input)
{
    string[] output;
    int offset, ptr = 0;

    while (ptr < input.length)
    {
	offset = ptr;
	/* Loop through until space found */
	while (ptr != input.length && !isspace (input[ptr]))
	    ++ptr;

	output ~= input[offset .. ptr];
	/* Ignore any other spaces found */
	while (ptr != input.length && isspace (input[ptr]))
	    ++ptr;
    }

    return output;
}

/* Helper Functions */
/* If compiled with -fversion=strict, asserts runtime instead of warning messages.
   Similarly, if compiled with -fdebug, debug messages are outputted */
void unknown_transaction (string code)
{
    string errstring = "Unknown transaction code: " ~ code;

    version (strict)
	assert (0, errstring);
    else
	fwritefln(stderr, errstring);
}


void try_withdraw (string account, ref long balance, long amount)
{
    string errstring = "Account '" ~ account ~ "' overdrawn, cannot continue";
    long result = balance - amount;

    version (strict)
	assert (result > 0, errstring);
    else
    {
	if (result < 0)
	{
	    fwritefln(stderr, errstring);
	    return;
	}
    }
    debug writefln ("WITHDRAWN £%s from %s. BALANCE £%s", amount, account, result);
    balance = result;
}


void try_deposit (string account, ref long balance, long amount)
{
    long result = balance + amount;

    debug writefln ("DEPOSITED £%s to %s. BALANCE £%s", amount, account, result);
    balance = result;
}


void try_deduct (string account, ref long balance, long amount)
{
    long result = balance - amount;

    debug writefln ("DEDUCTED £%s from %s. BALANCE £%s", amount, account, result);
    balance = result;
}


bool invalid_line(int length, string line)
{
    string errstring = "Invalid line syntax '" ~ line ~ "'";

    version (strict)
	assert (length == 3, errstring);
    else
    {
	if (length != 3)
	{
	    fwritefln(stderr, errstring);
	    return true;
	}
    }

    return false;
}


int main (string[] args)
{
    /* Using an associative array to hold account balances.
       This has the advantage of virtually unlimited storage space */
    long[string] accounts;

    /* No file argument given, just read from stdin then */
    if (args.length == 1)
	args ~= "/dev/stdin";

    /* Open file for reading, and parse by line, then by spaces,
       then case the transaction string and process accordingly */
    for (int i = 1; i < args.length; ++i)
    {
	string input = cast (string)read (args[i]);

	for (int ptr = 0; ptr < input.length; ++ptr)
	{
	    string line;
	    string[] toks;

	    line = get_line (input[ptr .. $]);
	    toks = split_spaces (line);
	    ptr += line.length;

	    if (invalid_line (toks.length, line))
		continue;
	    
	    switch (toks[ACTION])
	    {
		case "wd":
		case "cred":
		    try_withdraw (toks[ID], accounts[toks[ID]], toLong (toks[AMOUNT]));
		    break;

		case "dep":
		case "deb":
		    try_deposit (toks[ID], accounts[toks[ID]], toLong (toks[AMOUNT]));
		    break;

		case "fee":
		    try_deduct (toks[ID], accounts[toks[ID]], toLong (toks[AMOUNT]));
		    break;

		default:
		    unknown_transaction (toks[ACTION]);
	    }
	}
    }

    /* Loop through and output all accounts at end of runtime */
    writefln("-- End of Input Report --");
    foreach (account, balance; accounts)
	writefln("Account: %s\tBalance: £%s", account, balance);

    return 0;
}

```
To keep track of all account deposit and withdrawals, I use an associative dynamic array. So the cap limit of how many accounts you can store in runtime is practically unlimited.

To compile, cflag optimisations aren't really needed in this challenge, however, you will probably see an 8% increase in performance if you use -O2. :)
```
gdc -O2 challenge13.d
```
To compile with debug info:
```
gdc -fdebug challenge13.d
```
And to compile with strict / pedantic runtime (program asserts when it hits a syntax error).
```
gdc -fversion=strict challenge13.d
```

There is no file output, it reads from input and dumps to output. If I get round to it... probably do a persistent database file.


Update 1:
Some general speed optimisations. Should be 2-3 times quicker now I've dropped std.regexp. :)
Update 2:
Replaced D-style commments for C-style comments, in case it confuses anyone.
Update 3:
More speed optimisations. Shave 10% or maybe slightly more depending on how large the processing list is.

Regards

---

### Post by Notarika on 2010-06-06
To clarify, according to the contest rules, does using the stl iterator violate the rules? E.g.

```

int FindAccountIndex(int AccountID)
{
    int Index = -1;

    vector<Account>::iterator iter = AccountList.begin();

    // Look through the list for the account that has a matching id
    for (; iter != AccountList.end(); iter++)
    {
        // If it matches, return the index
        if ( (*iter).AccountID == AccountID )
            return distance(AccountList.begin(), iter);
    }

    return Index;
}

```

---

### Post by ibuclaw on 2010-06-06
@texaswriter.

If Notarika writes a C++ implementation, do let us know just how well it competes against the D implementation. :)

Regards.

---

### Post by schauerlich on 2010-06-07
I'll get around it commenting it later.

```
[color=#008000]**import**[/color] [color=#0000FF]**sys**[/color]

[color=#008000]**class**[/color] [color=#0000FF]**Account**[/color]:
    [color=#008000]**def**[/color] [color=#0000FF]__init__[/color]([color=#008000]self[/color], idnum):
        [color=#008000]self[/color][color=#666666].[/color]__idnum [color=#666666]=[/color] idnum
        [color=#008000]self[/color][color=#666666].[/color]__balance [color=#666666]=[/color] [color=#666666]0[/color]
        [color=#008000]self[/color][color=#666666].[/color]__fee_amount [color=#666666]=[/color] [color=#666666]10[/color]
        
        [color=#008000]self[/color][color=#666666].[/color]__actions [color=#666666]=[/color] {
            [color=#BA2121]"wd"[/color]   : [color=#008000]self[/color][color=#666666].[/color]__wd,
            [color=#BA2121]"dep"[/color]  : [color=#008000]self[/color][color=#666666].[/color]__dep,
            [color=#BA2121]"cred"[/color] : [color=#008000]self[/color][color=#666666].[/color]__cred,
            [color=#BA2121]"deb"[/color]  : [color=#008000]self[/color][color=#666666].[/color]__deb,
            [color=#BA2121]"fee"[/color]  : [color=#008000]self[/color][color=#666666].[/color]__fee,
        }
        
        
    [color=#008000]**def**[/color] [color=#0000FF]idnum[/color]([color=#008000]self[/color]):
        [color=#008000]**return**[/color] [color=#008000]self[/color][color=#666666].[/color]__idnum
        
    
    [color=#008000]**def**[/color] [color=#0000FF]balance[/color]([color=#008000]self[/color]):
        [color=#008000]**return**[/color] [color=#008000]self[/color][color=#666666].[/color]__balance
        
        
    [color=#008000]**def**[/color] [color=#0000FF]process[/color]([color=#008000]self[/color], action, amount):
        [color=#008000]**try**[/color]:
            amount [color=#666666]=[/color] [color=#008000]float[/color](amount)
            [color=#008000]**if**[/color] amount [color=#666666]>[/color] [color=#666666]0[/color]:
                [color=#008000]**return**[/color] [color=#008000]self[/color][color=#666666].[/color]__actions[action](amount)
            [color=#008000]**else**[/color]:
                [color=#008000]**print**[/color] [color=#BA2121]"Negative values are not accepted. Skipping."[/color]
                [color=#008000]**return**[/color] [color=#008000]None[/color]
                
        [color=#008000]**except**[/color] [color=#D2413A]**ValueError**[/color]:
            [color=#008000]**print**[/color] [color=#BA2121]"Invalid argument for action. Skipping."[/color]
            [color=#008000]**return**[/color] [color=#008000]None[/color]
            
        [color=#008000]**except**[/color] [color=#D2413A]**IndexError**[/color]:
            [color=#008000]**print**[/color] [color=#BA2121]"Unrecognized command. Skipping."[/color]
            [color=#008000]**return**[/color] [color=#008000]None[/color]
      
            
    [color=#008000]**def**[/color] [color=#0000FF]__wd[/color]([color=#008000]self[/color], amount):
        [color=#008000]**if**[/color] [color=#008000]self[/color][color=#666666].[/color]__balance [color=#666666]<[/color] [color=#666666]0[/color]:
            [color=#008000]**print**[/color] [color=#BA2121]"Your account is already overdrawn. Please deposit"[/color]
            [color=#008000]**print**[/color] [color=#BA2121]"something before attempting another withdrawal."[/color]
            [color=#008000]**return**[/color] [color=#008000]None[/color]
            
        [color=#008000]**elif**[/color] [color=#008000]self[/color][color=#666666].[/color]__balance [color=#666666]>=[/color] amount:
            [color=#008000]**print**[/color] [color=#BA2121]"Withdrawing $[/color][color=#BB6688]**%.2f**[/color][color=#BA2121] from account [/color][color=#BB6688]**%d**[/color][color=#BA2121]."[/color] \
                    [color=#666666]%[/color] (amount, [color=#008000]self[/color][color=#666666].[/color]__idnum)
            [color=#008000]self[/color][color=#666666].[/color]__balance [color=#666666]-=[/color] amount
            [color=#008000]**return**[/color] [color=#008000]self[/color][color=#666666].[/color]__balance
            
        [color=#008000]**else**[/color]:
            [color=#008000]**print**[/color] [color=#BA2121]"Overdraft on account [/color][color=#BB6688]**%d**[/color][color=#BA2121]."[/color] [color=#666666]%[/color] [color=#008000]self[/color][color=#666666].[/color]__idnum
            [color=#008000]**print**[/color] [color=#BA2121]"Attempted to withdraw $[/color][color=#BB6688]**%.2f**[/color][color=#BA2121] with only $[/color][color=#BB6688]**%.2f**[/color][color=#BA2121] remaining."[/color] \
                    [color=#666666]%[/color] (amount, [color=#008000]self[/color][color=#666666].[/color]__balance)
            [color=#008000]**return**[/color] [color=#008000]self[/color][color=#666666].[/color]__fee([color=#008000]self[/color][color=#666666].[/color]__fee_amount)
    
    
    [color=#008000]**def**[/color] [color=#0000FF]__dep[/color]([color=#008000]self[/color], amount):
        [color=#008000]**print**[/color] [color=#BA2121]"Depositing $[/color][color=#BB6688]**%.2f**[/color][color=#BA2121] into account [/color][color=#BB6688]**%d**[/color][color=#BA2121]."[/color] \
                [color=#666666]%[/color] (amount, [color=#008000]self[/color][color=#666666].[/color]__idnum)
        [color=#008000]self[/color][color=#666666].[/color]__balance [color=#666666]+=[/color] amount
        [color=#008000]**return**[/color] [color=#008000]self[/color][color=#666666].[/color]__balance
    
    
    [color=#008000]**def**[/color] [color=#0000FF]__cred[/color]([color=#008000]self[/color], amount):
        [color=#008000]**return**[/color] [color=#008000]self[/color][color=#666666].[/color]__wd(amount)
    
    
    [color=#008000]**def**[/color] [color=#0000FF]__deb[/color]([color=#008000]self[/color], amount):
        [color=#008000]**return**[/color] [color=#008000]self[/color][color=#666666].[/color]__dep(amount)
    
    
    [color=#008000]**def**[/color] [color=#0000FF]__fee[/color]([color=#008000]self[/color], amount):
        [color=#008000]**print**[/color] [color=#BA2121]"Assessing a fee of $[/color][color=#BB6688]**%.2f**[/color][color=#BA2121] on account [/color][color=#BB6688]**%d**[/color][color=#BA2121]."[/color] \
                [color=#666666]%[/color] (amount, [color=#008000]self[/color][color=#666666].[/color]__idnum)
        [color=#008000]self[/color][color=#666666].[/color]__balance [color=#666666]-=[/color] amount
        [color=#008000]**return**[/color] [color=#008000]self[/color][color=#666666].[/color]__balance
  
  
      
[color=#008000]**def**[/color] [color=#0000FF]main[/color]():
    accounts [color=#666666]=[/color] {}
    
    [color=#008000]**while**[/color] [color=#008000]True[/color]:        
        command [color=#666666]=[/color] sys[color=#666666].[/color]stdin[color=#666666].[/color]readline()[color=#666666].[/color]split()
        
        [color=#008000]**if**[/color] [color=#AA22FF]**not**[/color] command:
            [color=#008000]**break**[/color]
        
        action [color=#666666]=[/color] command[[color=#666666]0[/color]]
        accountnum [color=#666666]=[/color] command[[color=#666666]1[/color]]
        amount [color=#666666]=[/color] command[[color=#666666]2[/color]]
        
        [color=#008000]**try**[/color]:
            accountnum [color=#666666]=[/color] [color=#008000]int[/color](accountnum)
        [color=#008000]**except**[/color] [color=#D2413A]**ValueError**[/color]:
            [color=#008000]**print**[/color] [color=#BA2121]"Invalid account number. Skipping."[/color]
            [color=#008000]**continue**[/color]
        
        [color=#008000]**if**[/color] accountnum [color=#AA22FF]**not**[/color] [color=#AA22FF]**in**[/color] accounts:
            [color=#008000]**if**[/color] action [color=#666666]==[/color] [color=#BA2121]"dep"[/color] [color=#AA22FF]**or**[/color] action [color=#666666]==[/color] [color=#BA2121]"deb"[/color]:
                [color=#008000]**try**[/color]:
                    accounts[accountnum] [color=#666666]=[/color] Account(accountnum)
                    [color=#008000]**print**[/color] [color=#BA2121]"Created new account: ID number [/color][color=#BB6688]**%d**[/color][color=#BA2121]"[/color] [color=#666666]%[/color] accountnum
                [color=#008000]**except**[/color]:
                    [color=#008000]**print**[/color] [color=#BA2121]"Couldn't create new account [/color][color=#BB6688]**%d**[/color][color=#BA2121]."[/color] [color=#666666]%[/color] accountnum
                    [color=#008000]**print**[/color] [color=#BA2121]"Think long and hard about what you've done."[/color]
                    [color=#008000]**print**[/color]
                    [color=#008000]**continue**[/color]
            [color=#008000]**else**[/color]:
                [color=#008000]**print**[/color] [color=#BA2121]"Can't withdraw from non-existant account [/color][color=#BB6688]**%d**[/color][color=#BA2121]."[/color] \
                        [color=#666666]%[/color] accountnum
                [color=#008000]**print**[/color]
                [color=#008000]**continue**[/color]
                        
        balance [color=#666666]=[/color] accounts[accountnum][color=#666666].[/color]process(action, amount)
        
        [color=#008000]**if**[/color] balance [color=#666666]!=[/color] [color=#008000]None[/color]:
            [color=#008000]**print**[/color] [color=#BA2121]"Account: [/color][color=#BB6688]**%d**[/color][color=#BA2121]. Current Balance: $[/color][color=#BB6688]**%.2f**[/color][color=#BA2121]."[/color] \
                    [color=#666666]%[/color] (accountnum, balance)
        [color=#008000]**print**[/color]
        
        
    [color=#008000]**print**[/color]
    [color=#008000]**print**[/color] [color=#BA2121]"Final tally:"[/color]
    
    [color=#008000]**for**[/color] idnum [color=#AA22FF]**in**[/color] accounts[color=#666666].[/color]keys():
        [color=#008000]**print**[/color] [color=#BA2121]"Account: [/color][color=#BB6688]**%d**[/color][color=#BB6622]**\t**[/color][color=#BA2121]Balance: $[/color][color=#BB6688]**%.2f**[/color][color=#BA2121]"[/color] \
                [color=#666666]%[/color] (idnum, accounts[idnum][color=#666666].[/color]balance())
    
    [color=#008000]**print**[/color]                
    [color=#008000]**print**[/color] [color=#BA2121]"Exiting. Have a nice day, I guess."[/color]  
        
[color=#008000]**if**[/color] __name__ [color=#666666]==[/color] [color=#BA2121]"__main__"[/color]:
    [color=#008000]**try**[/color]:
        main()
    [color=#008000]**except**[/color] [color=#D2413A]**KeyboardInterrupt**[/color]:
        [color=#008000]**print**[/color] [color=#BA2121]"Fine, leave early."[/color]
        sys[color=#666666].[/color]exit([color=#666666]0[/color])

```

Tested with:

```

wd 10 293.60
cred 5 808.60
wd 4 536.10
cred 5 816.70
deb 2 692.10
wd 4 586.20
cred 1 685.80
dep 8 659.70
deb 5 450.80
deb 9 931.00
deb 9 704.50
cred 3 231.70
cred 10 972.00
wd 2 772.20
wd 6 955.30
wd 1 172.50
dep 2 108.40
deb 10 139.30
deb 7 510.00
wd 1 78.00
dep 5 500.60
wd 8 401.90
deb 1 42.00
cred 1 583.20
deb 3 676.80
dep 1 198.00
wd 5 849.30
dep 3 153.20
deb 2 921.30
cred 6 25.80
deb 7 922.30
deb 4 613.60
wd 6 511.80
dep 3 921.90
cred 7 191.70
wd 7 903.50
dep 10 361.80
deb 5 892.10
wd 3 807.40
deb 9 146.70
deb 2 499.00
cred 9 5.00
deb 6 904.20
cred 9 660.60
wd 7 767.00
wd 2 1.60
dep 1 815.50
cred 10 135.70
dep 1 964.00
cred 9 9.80
dep 6 806.30
deb 9 324.60
cred 2 763.60
dep 5 85.60
dep 9 779.40
deb 6 226.90
deb 6 125.90
dep 1 551.70
wd 4 119.40
dep 10 677.80
deb 1 515.70
dep 4 87.80
wd 10 360.40
wd 7 573.20
cred 8 115.90
cred 7 256.30
wd 4 502.80
cred 1 255.90
wd 10 221.70
deb 2 430.60
wd 4 246.70
wd 9 513.20
wd 2 993.60
wd 2 924.10
dep 1 565.70
wd 9 804.20
deb 2 587.20
cred 2 638.60
deb 8 423.40
wd 5 55.80
dep 5 316.40
cred 4 158.30
deb 3 461.50
deb 7 903.20
dep 4 944.30
cred 7 28.50
wd 3 55.40
wd 8 584.30
cred 5 745.10
wd 1 577.30
wd 9 240.40
wd 5 352.80
wd 6 106.10
cred 2 793.20
deb 10 535.40
cred 6 607.40
wd 1 895.90
cred 9 5.60
deb 1 371.40
wd 9 578.80
fee 5 527.20
fee 2 96.10
fee 9 923.40
fee 5 206.50
fee 4 151.20
fee 1 363.40
fee 7 203.60
fee 8 741.10
fee 7 324.50
fee 4 177.20
dep 10 453.40

```

Results:

```
Final tally:
Account: 1	Balance: $1921.50
Account: 2	Balance: $-68.10
Account: 3	Balance: $1350.60
Account: 4	Balance: $675.10
Account: 5	Balance: $-491.20
Account: 6	Balance: $1349.80
Account: 7	Balance: $407.40
Account: 8	Balance: $-185.80
Account: 9	Balance: $-854.80
Account: 10	Balance: $1449.90


```

---

### Post by lisati on 2010-06-07
> **texaswriter said:**
> 
lisati> Those have built-in capabilities that break that rule. That said, a list by itself or something similar WOULD be fine as long as you never resize it or use built-in functions/libraries to fulfill the challenges laid out.


Huh? I wasn't think of lists, but of debit and credit.

In a real-world bookkeeping system......

---

### Post by lavinog on 2010-06-07
> **schauerlich said:**
> I honestly haven't tested it much, but I think it works.

```
[color=#008000]**import**[/color] [color=#0000FF]**sys**[/color]

[color=#008000]**class**[/color] [color=#0000FF]**Account**[/color]:
    [color=#008000]**def**[/color] [color=#0000FF]__init__[/color]([color=#008000]self[/color], idnum):
        [color=#008000]self[/color][color=#666666].[/color]__idnum [color=#666666]=[/color] idnum
        [color=#008000]self[/color][color=#666666].[/color]__balance [color=#666666]=[/color] [color=#666666]0[/color]
        [color=#008000]self[/color][color=#666666].[/color]__fee_amount [color=#666666]=[/color] [color=#666666]10[/color]
        
        [color=#008000]self[/color][color=#666666].[/color]__actions [color=#666666]=[/color] {
            [color=#BA2121]"wd"[/color]   : [color=#008000]self[/color][color=#666666].[/color]__wd,
            [color=#BA2121]"dep"[/color]  : [color=#008000]self[/color][color=#666666].[/color]__dep,
            [color=#BA2121]"cred"[/color] : [color=#008000]self[/color][color=#666666].[/color]__cred,
            [color=#BA2121]"deb"[/color]  : [color=#008000]self[/color][color=#666666].[/color]__deb,
            [color=#BA2121]"fee"[/color]  : [color=#008000]self[/color][color=#666666].[/color]__fee,
        }

```

Does assigning __actions in the class initializer waste memory when there are multiple Account objects?
Won't there be multiple copies of this list for each account?

Also how did you add the color? (did you manually do it, or is there a tool?)

---

### Post by schauerlich on 2010-06-07
> **lavinog said:**
> Does assigning __actions in the class initializer waste memory when there are multiple Account objects?
Won't there be multiple copies of this list for each account?

I'm calling instance methods, so the dictionary containing them has to be an instance variable.

> Also how did you add the color? (did you manually do it, or is there a tool?)

[http://www.challenge-you.com/bbcode](http://www.challenge-you.com/bbcode)

---

### Post by texaswriter on 2010-06-07
> **lisati said:**
> Huh? I wasn't think of lists, but of debit and credit.

In a real-world bookkeeping system......

Yeah, strike the part about not having a resizeable array. I think I edited that out, if not you can use a resizeable array. I will only create 200 account numbers in my test and will only expect 200 to be created. Nobody has to implement a static limit, however. Please read the rest of this post to understand why. Otherwise, your code is fine. 


Notarika> > **Notarika said:**
> To clarify, according to the contest rules, does using the stl iterator violate the rules? E.g.



OK, from what I see, is not 'iter' similar to the list with comparable built-in functions accompanying it? If so, it is acceptable given the same restrictions set for the other one. Simple built-in functions are acceptable such as insert, append... 

So yes, that is acceptable. 


For everybody else too> 
Anyways, for others as well, after anybody uploads code, within 24 hours I will test your code. Then I will PM you on how the program handled everything, general comments, as well as the time it took to handle 2100 random. The real final test will include something like 10,000 or 20,000 randomly generated transactions. 

How verbose the program is varies on the programmers tastes as long as, at the very least, the end balance of the accounts is apparent. Even just printing the balance at the end of each transaction would work perfectly. One person just printed the balances at the very end. Either of these implementations is fine. 

Finally, just a quick bit about judging. Although most of the categories will be more or less pass/fail, which will be a cursory glance for me, one category will be looked at much closer. I have simply divided the points among each category [25% each] and then the extra credit [20% extra]. The hash key will be challenging, though rewarding to learn and for judging consideration. **[COLOR=Red]Edit: in light of recent changes to make this challenge more beginner friendly, how much someone learns/grows with their program will be considered. It's hard to really elaborate on this, but needless to say it's of benefit to any programmers poking their head into the world of programming. [/COLOR]**

To summarize the above again, most people *should* get 75% of the points. If you use a hash key to store/retrieve account numbers and/or balances you will be simply awarded the 20% [supposing it is genuinely used]. Otherwise, the contest will come down to time. 

The only one worth mentioning in detail is the time. Here is exactly how I will judge who gets what for their time. First off, I will make a file with 10,000 or 20,000 account numbers. I will have transactions for non-existing account numbers. If an account number doesn't exist AND the transaction is not a deposit [or something that does the same thing], the account number should **not be created**. I will put alot of non-existent account numbers in there and I will put a penalty in this category if account numbers are just blindly created. I'm really testing how fast your subroutine searches for account numbers and the only way to really test it is to see how long it takes to go through all your account numbers [if applicable].

Anyways, so let's say we have the following times for processing the file: 

Person 1: 5 seconds
Person 2: 4 seconds
Person 3: 2 seconds
Person 4: .5 seconds
Person 5: .6 seconds

Person 4 has the lowest time and will be awarded 100% of points for this category. Here is how the rest's points will be calculated. 

Person 1: 1/(5/.5) = 10%
Person 2: 1/(4/.5) = 12.5%
Person 3: 1/(2/.5) = 25%
Person 4: 1/(.5/.5)= 100%
Person 5: 1/(.6/.5)= 83.3%

Please note: I will post everybody's times [possibly anonymously, as in just a list of times] one week before the competition ends to give people a chance to possibly change. Since I would have PM'ed you your time(s), you can easily know what score you will get here. 

Like I said, this will be the only category that will be assessed technically, the rest are essentially pass fail. I want the challenge to be a learning experience, and if you wrote good, readable, straight-forward code, I want you to know this. I'm not trying to nit-pick anyone. The speed is important however. 

That said, kudos to those who have submitted code so far and I look forward to seeing more novel implementations by others. 

Keep up the great work!!

---

### Post by dv3500ea on 2010-06-07
@schauerlich, I like how your bank has an overdraft charge!

> **texaswriter said:**
> If an account number doesn't exist AND the transaction is not a deposit [or something that does the same thing], the account number should **not be created**. I will put alot of non-existent account numbers in there and I will put a penalty in this category if account numbers are just blindly created.

My current program does create accounts if they don't exist. How will the list of valid accounts be made available to the program? Will the file be passed in as a filename as a command line argument or something different?

---

### Post by dv3500ea on 2010-06-07
Here is a perl version that is significantly faster than my ruby version (though a bit uglier too). This version does not create accounts out of thin air like the other one did:

```
[color=#408080]*#!/usr/bin/env perl*[/color]
[color=#408080]*#*[/color]
[color=#408080]*#       challenge13.pl*[/color]
[color=#408080]*#       *[/color]
[color=#408080]*#       Copyright 2010*[/color]
[color=#408080]*#       *[/color]
[color=#408080]*#       This program is free software; you can redistribute it and/or modify*[/color]
[color=#408080]*#       it under the terms of the GNU General Public License as published by*[/color]
[color=#408080]*#       the Free Software Foundation; either version 2 of the License, or*[/color]
[color=#408080]*#       (at your option) any later version.*[/color]
[color=#408080]*#       *[/color]
[color=#408080]*#       This program is distributed in the hope that it will be useful,*[/color]
[color=#408080]*#       but WITHOUT ANY WARRANTY; without even the implied warranty of*[/color]
[color=#408080]*#       MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the*[/color]
[color=#408080]*#       GNU General Public License for more details.*[/color]
[color=#408080]*#       *[/color]
[color=#408080]*#       You should have received a copy of the GNU General Public License*[/color]
[color=#408080]*#       along with this program; if not, write to the Free Software*[/color]
[color=#408080]*#       Foundation, Inc., 51 Franklin Street, Fifth Floor, Boston,*[/color]
[color=#408080]*#       MA 02110-1301, USA.*[/color]

[color=#008000]**use**[/color] strict;
[color=#008000]**use**[/color] warnings;

[color=#408080]*#if --speed is given as the first argument, the program will go as fast as it can*[/color]
[color=#408080]*#if --debug is given the program will print the balance after each transaction*[/color]
[color=#408080]*#otherwise the program will just try to make the results look nice*[/color]

[color=#008000]**my**[/color] [color=#19177C]$mode[/color] [color=#666666]=[/color] [color=#666666]2[/color];
[color=#008000]**if**[/color] ([color=#19177C]$ARGV[/color][[color=#666666]0[/color]] [color=#AA22FF]**eq**[/color] [color=#BA2121]'--debug'[/color]) {
	[color=#19177C]$mode[/color] [color=#666666]=[/color] [color=#666666]1[/color];
} [color=#008000]**elsif**[/color] ([color=#19177C]$ARGV[/color][[color=#666666]0[/color]] [color=#AA22FF]**eq**[/color] [color=#BA2121]'--speed'[/color]) {
	[color=#19177C]$mode[/color] [color=#666666]=[/color] [color=#666666]0[/color];
}

[color=#008000]**my**[/color] [color=#19177C]%accounts[/color] [color=#666666]=[/color] ();[color=#408080]*#hash for storing/retrieving accounts*[/color]

[color=#008000]**sub **[/color][color=#0000FF]dep[/color] { [color=#408080]*#function to deposit money into account*[/color]
		[color=#008000]**my**[/color] ([color=#19177C]$account[/color], [color=#19177C]$amount[/color]) [color=#666666]=[/color] [color=#19177C]@_[/color];[color=#408080]*#arguments - account_number, amount*[/color]
		[color=#008000]**if**[/color] ([color=#008000]exists[/color] [color=#19177C]$accounts[/color]{[color=#19177C]$account[/color]}) {[color=#408080]*#if account exists*[/color]
				[color=#19177C]$accounts[/color]{[color=#19177C]$account[/color]} [color=#666666]+=[/color] [color=#19177C]$amount[/color]; [color=#408080]*#add deposit amount to account balance*[/color]
		} [color=#008000]**else**[/color] {[color=#408080]*#if account doesn't exist*[/color]
				[color=#19177C]$accounts[/color]{[color=#19177C]$account[/color]} [color=#666666]=[/color] [color=#19177C]$amount[/color]; [color=#408080]*#create account with balance amount*[/color]
		}
		[color=#008000]**return**[/color] [color=#19177C]$accounts[/color]{[color=#19177C]$account[/color]}; [color=#408080]*#return new balance*[/color]
}

[color=#008000]**sub **[/color][color=#0000FF]fee[/color] { [color=#408080]*#function to charge a fee to the account*[/color]
		[color=#008000]**my**[/color] ([color=#19177C]$account[/color], [color=#19177C]$amount[/color]) [color=#666666]=[/color] [color=#19177C]@_[/color];[color=#408080]*#arguments - account_number, amount*[/color]
		[color=#008000]**if**[/color] ([color=#008000]exists[/color] [color=#19177C]$accounts[/color]{[color=#19177C]$account[/color]}) {[color=#408080]*#if account exists*[/color]
				[color=#19177C]$accounts[/color]{[color=#19177C]$account[/color]} [color=#666666]-=[/color] [color=#19177C]$amount[/color]; [color=#408080]*#take fee amount from account balance*[/color]
		} [color=#008000]**else**[/color] {[color=#408080]*#if account doesn't exist*[/color]
				[color=#008000]warn[/color] [color=#BA2121]"What do you mean '$account', there is no such account!\n"[/color];
		}
		[color=#008000]**return**[/color] [color=#19177C]$accounts[/color]{[color=#19177C]$account[/color]}; [color=#408080]*#return new balance*[/color]
}

[color=#008000]**sub **[/color][color=#0000FF]wd[/color] { [color=#408080]*#function to withdraw from account*[/color]
		[color=#008000]**my**[/color] ([color=#19177C]$account[/color], [color=#19177C]$amount[/color]) [color=#666666]=[/color] [color=#19177C]@_[/color];[color=#408080]*#arguments - account_number, amount*[/color]
		[color=#008000]**if**[/color] ([color=#008000]exists[/color] [color=#19177C]$accounts[/color]{[color=#19177C]$account[/color]}) {[color=#408080]*#if account exists*[/color]
				[color=#008000]**if**[/color] ([color=#19177C]$accounts[/color]{[color=#19177C]$account[/color]} [color=#666666]>=[/color] [color=#19177C]$amount[/color]) {[color=#408080]*#only succeed if enough balance*[/color]
					[color=#19177C]$accounts[/color]{[color=#19177C]$account[/color]} [color=#666666]-=[/color] [color=#19177C]$amount[/color]; [color=#408080]*#take fee amount from account balance*[/color]
				} [color=#008000]**else**[/color] {
					[color=#008000]warn[/color] [color=#BA2121]"You can't withdraw $amount if you only have $accounts{$account}!\n"[/color];
				}
		} [color=#008000]**else**[/color] {[color=#408080]*#if account doesn't exist*[/color]
				[color=#008000]warn[/color] [color=#BA2121]"What do you mean '$account', there is no such account!\n"[/color];
		}
		[color=#008000]**return**[/color] [color=#19177C]$accounts[/color]{[color=#19177C]$account[/color]}; [color=#408080]*#return new balance	*[/color]
}

[color=#008000]**sub **[/color][color=#0000FF]parse[/color] {
		[color=#008000]**my**[/color] [color=#19177C]$str[/color] [color=#666666]=[/color] [color=#008000]shift[/color];
		[color=#008000]**my**[/color] ([color=#19177C]$trans[/color], [color=#19177C]$account[/color], [color=#19177C]$amount[/color]) [color=#666666]=[/color] [color=#008000]split[/color]([color=#BA2121]' '[/color], [color=#19177C]$str[/color]);
		[color=#408080]*#parse transaction_type account_num amount*[/color]
		[color=#19177C]$amount[/color] [color=#666666]+=[/color] [color=#666666]0[/color]; [color=#408080]*#turn amount into a number*[/color]
		[color=#19177C]$account[/color] [color=#666666]+=[/color] [color=#666666]0[/color]; 
		[color=#408080]*#ensure account is a number. This ensures numerical sorting of accounts as a opposed to alphabetical*[/color]
		[color=#008000]**if**[/color] ([color=#19177C]$trans[/color] [color=#AA22FF]**eq**[/color] [color=#BA2121]'wd'[/color] [color=#666666]||[/color] [color=#19177C]$trans[/color] [color=#AA22FF]**eq**[/color] [color=#BA2121]'cred'[/color]) {[color=#408080]*#withdraw commands*[/color]
				[color=#008000]**return**[/color] wd([color=#19177C]$account[/color], [color=#19177C]$amount[/color]);
		} [color=#008000]**elsif**[/color] ([color=#19177C]$trans[/color] [color=#AA22FF]**eq**[/color] [color=#BA2121]'fee'[/color]) {[color=#408080]*#fee command*[/color]
				[color=#008000]**return**[/color] fee([color=#19177C]$account[/color], [color=#19177C]$amount[/color]);
		} [color=#008000]**elsif**[/color] ([color=#19177C]$trans[/color] [color=#AA22FF]**eq**[/color] [color=#BA2121]'dep'[/color] [color=#666666]||[/color] [color=#19177C]$trans[/color] [color=#AA22FF]**eq**[/color] [color=#BA2121]'deb'[/color]) {[color=#408080]*#deposit commands*[/color]
				[color=#008000]**return**[/color] dep([color=#19177C]$account[/color], [color=#19177C]$amount[/color]);
		} [color=#008000]**else**[/color] {[color=#408080]*#warning on incorrect commands*[/color]
				[color=#008000]warn[/color] [color=#BA2121]"'$trans' is not a transaction I understand! I do understand:\n
	dep or deb = where money is put in
	wd or cred = where money is taken out (as long as you have enough)
	fee = where money is taken out (even if you don't have enough)\n"[/color];
		} 
		[color=#008000]**return**[/color] [color=#BA2121]'0'[/color];
}

[color=#008000]**if**[/color] ([color=#19177C]$mode[/color] [color=#666666]==[/color] [color=#666666]1[/color]) {[color=#408080]*#debug*[/color]
	[color=#008000]**while**[/color] ([color=#666666]<[/color][color=#008000]STDIN[/color][color=#666666]>[/color]) {[color=#408080]*#loop over input*[/color]
		[color=#008000]**print**[/color] [color=#BA2121]"BALANCE: £"[/color] [color=#666666].[/color] parse([color=#19177C]$_[/color]) [color=#666666].[/color] [color=#BA2121]"\n"[/color];[color=#408080]*#apply transactions and print new balance*[/color]
	} 
} [color=#008000]**else**[/color] {
	[color=#008000]**while**[/color] ([color=#666666]<[/color][color=#008000]STDIN[/color][color=#666666]>[/color]) {[color=#408080]*#loop over input*[/color]
		parse([color=#19177C]$_[/color]);
	} 
}

[color=#008000]**print**[/color] [color=#BA2121]"-"[/color] x [color=#666666]33[/color] [color=#666666].[/color] [color=#BA2121]"\n"[/color];

[color=#008000]**if**[/color] ([color=#19177C]$mode[/color]) {
		[color=#008000]**foreach**[/color] ([color=#008000]sort[/color] {[color=#19177C]$a[/color] [color=#666666]<=>[/color] [color=#19177C]$b[/color]} [color=#008000]keys[/color]([color=#19177C]%accounts[/color])) {
			[color=#008000]**print**[/color] [color=#BA2121]"Account: $_   Balance: £$accounts{$_}\n"[/color];
		}
} [color=#008000]**else**[/color] {[color=#408080]*#speed*[/color]
		[color=#008000]**foreach**[/color] ([color=#008000]keys[/color]([color=#19177C]%accounts[/color])) {
			[color=#008000]**print**[/color] [color=#BA2121]"Account: $_   Balance: £$accounts{$_}\n"[/color];
		}
}

```

I've tested it along side the other versions using a randomly generated file of 100000 transactions and 9 accounts. For some reason all gave slightly different end values. I can't work out why.

Here are the final values from my generated file:

```

D:
Account: 0   Balance: £1802
Account: 1   Balance: £121082
Account: 2   Balance: £49366
Account: 3   Balance: £82473
Account: 4   Balance: £85320
Account: 5   Balance: £30468
Account: 6   Balance: £8256
Account: 7   Balance: £83802
Account: 8   Balance: £133931
time:
real	0m0.700s
user	0m0.644s
sys	0m0.052s


perl:
Account: 0   Balance: £1802
Account: 1   Balance: £121082
Account: 2   Balance: £49366
Account: 3   Balance: £82482
Account: 4   Balance: £85327
Account: 5   Balance: £30468
Account: 6   Balance: £8287
Account: 7   Balance: £83802
Account: 8   Balance: £133931
time:
real	0m5.260s
user	0m0.568s
sys	0m0.232s


python:
Account: 0   Balance: £1886.0
Account: 1   Balance: £121012.0
Account: 2   Balance: £49427.0
Account: 3   Balance: £82461.0
Account: 4   Balance: £85291.0
Account: 5   Balance: £30552.0
Account: 6   Balance: £8262.0
Account: 7   Balance: £83858.0
Account: 8   Balance: £134224.0
time:
real	0m16.346s
user	0m1.556s
sys	0m0.512s


ruby:
Account: 0   Balance: £1799.0
Account: 1   Balance: £120789.0
Account: 2   Balance: £49354.0
Account: 3   Balance: £81845.0
Account: 4   Balance: £85353.0
Account: 5   Balance: £30411.0
Account: 6   Balance: £8317.0
Account: 7   Balance: £83781.0
Account: 8   Balance: £133888.0
time:
real	1m11.668s
user	0m9.665s
sys	0m13.201s


```

---

### Post by ibuclaw on 2010-06-07
> **dv3500ea said:**
> 
I've tested it along side the D version and the python version. For some reason all 3 give slightly different end values. I can't work out why.


Oh the inconsistencies! :popcorn:

dv3500, if you compile the D code with -fdebug it will print out all calculations as it does it.

Do the same for Perl, and if an inconsistency crops up between return values, see what the number is and what the return value *should* be.

Regards

---

### Post by ibuclaw on 2010-06-07
Actually, I've just made a slight adjustment on my side, switched to longs instead of doubles. Probably loose some precision, but gains some more speed. :)

Regards

---

### Post by dv3500ea on 2010-06-07
On running the following for each program:
```

fee 1 1
deb 2 1
dep 3 1
wd 4 1
cred 5 1

```
I get:
```

D:
Account: 1	Balance: £-1
Account: 2	Balance: £1
Account: 3	Balance: £1
Account: 4	Balance: £0
Account: 5	Balance: £0

perl:
Account: 2   Balance: £1
Account: 3   Balance: £1

python:
Account: 2   Balance: £1.0
Account: 3   Balance: £1.0

ruby:
Account: 1   Balance: £-1.0
Account: 2   Balance: £1.0
Account: 3   Balance: £1.0
Account: 4   Balance: £0
Account: 5   Balance: £0



```
That explains some of the difference, although not the differences between the perl + python version and D + ruby. It's possible for the ruby version I forgot to clear /tmp files

Oh yeah, the python version charges 10 on overdraft.

---

### Post by texaswriter on 2010-06-07
> **dv3500ea said:**
> @schauerlich, I like how your bank has an overdraft charge!



My current program does create accounts if they don't exist. How will the list of valid accounts be made available to the program? Will the file be passed in as a filename as a command line argument or something different?

*Schauerlich>* Great questions: First off, don't worry about files being passed, though if built-in routines are already there you can leave them there [if you wish]... I will redirect input, so act like all input is going to come from the keyboard. 

I will specifically design the test file to only deposit money in 200 accounts. So, as was said above, ***no built-in checks need to be made on whether 200 accounts were entered*. **Essentially, just assume an account needs to be created when it doesn't exist & a deposit or debit is being made [i.e. money being put into the account].

*To everybody>* I do want to reiterate this: This **Beginner Programming Challenge ** was intended to teach people the use of hash keys by having beginners research hash keys and implement their own. To extend the challenge to people who don't feel comfortable doing this yet, any competitors who merely complete the functionality any way of their choosing are welcome as well. This competition is also to anyone who feels challenged, so if at first you just need to build the program without a hash routine, I welcome you to compete at the level you need to to properly learn. Afterwards, if you need further challenge, you can consider research hashing routines. 

If the scoring daunts you, just ignore it and enjoy learning and completing the challenge. Anybody who even participates has won because they have gained experience and otherwise learned. Since I will only be judging beginner's challenges, don't worry about your code not "measuring up". 

Otherwise, please enjoy your experience and I welcome more beginner programmers. 

*Non-beginner programmers> *If anybody feels they are not a beginner, you are feel to write code for the competition and even send it to me, but I would ask that inform me if you are an advanced programmer so I know who to consider. Also, if you are an advanced programmer try to restrain from submitting code *right away*. Wait a week or two before submitting code if you are a non-beginner. 

*Ibuclaw>* EDIT: I'm allowing these basic hash routines that seem to be built-in to many languages array functions. This doesn't count for extra credit. I highly recommend beginners first make their program with whatever storage/retrieval method they want, then afterwards try to make their own hashing routine just for the practice. This is a reversal of what was here previously. I had no idea so many languages implemented hash methods in basic arrays. This reversal is to make the competition as beginner-friendly as possible. I understand it can be daunting making a program that encompasses a lot of ground. Try  making a viable program using whatever account retrieval/storage method you can and then worry about trying different methods later. 

Good luck and have fun!!

---

### Post by dv3500ea on 2010-06-07
> **texaswriter said:**
> If anybody else is aware of a similarity in their code, I would ask that you inform me and/or reimplement this feature.

I'm not exactly sure what a hashing routine is, but perl has an inbuilt data type called a hash which consists of key/value pairs (I think this is the same as a ruby hash, a python dict or a javascript object). I have used this as the main storage/retrieval mechanism for accounts. The keys of the hash are account numbers and the values are balances.

> **ibuclaw said:**
> Actually, I've just made a slight adjustment on my side, switched to longs instead of doubles. Probably loose some precision, but gains some more speed. :)

I can't do that in perl - it decides for you what type (int/float) the number is. My main optimisation has been to not write to stdout until the end of the program. This makes a surprisingly large speed improvement; approximately by a factor of 10.

---

### Post by schauerlich on 2010-06-07
> **dv3500ea said:**
> I can't do that in perl - it decides for you what type (int/float) the number is. My main optimisation has been to not write to stdout until the end of the program. This makes a surprisingly large speed improvement; approximately by a factor of 10.

I/O is a huge time killer. I wasn't going for speed, I wanted to make it as clear as possible what transactions were and weren't performed, and why.

---

### Post by snova on 2010-06-07
> **schauerlich said:**
> I'm calling instance methods, so the dictionary containing them has to be an instance variable.

Not necessarily; if the dictionary is defined as a class variable then you can simply pass self explicitly to the methods.

---

### Post by texaswriter on 2010-06-08
This challenge has been a nice learning experience for me too, learning that all these languages implement hash keys for their built-in functions. Very impressive. 

Well, in the true spirit of my last post, I'll allow any of these as well. I wasn't aware that so many languages did this, and I can understand how many people would not "get" implementing this on their own. 

I wouldn't go out of your way to make speed improvements, especially if it ends up making your results inconsistent. Optimizations should be simple, where you know what the original code does and what exactly the replacement code will do, this way you can clearly be aware of any differences that will exist. 

The challenge of writing your own hash function would be valuable just for how this type of coding makes you think... about the uses of math to make code far more efficient... about trying different types of hash tables to see different results.

[COLOR=Red]**Edit: I made an addition to scoring to benefit any beginner challengers, so if you are unsure of yourself, feel free to go ahead and give the competition a go. If you aren't sure of the extra credit portion, first get the program working well with any account storage/retrieval method and then try your hand at implementing your own hash method. **

[COLOR=Black]Hash keys are a form of mathematical functions, also known as algorithmic programming. Even though some popular languages abstract this, it can be useful to know how to implement your own in case you come across a situation that would benefit greatly by a special implementation. BUT: I put this in for the beginner programmers just to see first hand what algorithmic programming is and how it can get your mind thinking about how to apply math to programming to greatly simplify things. Imagine this: The way you would do this other than a hash function is : a) a linear search [very slow] b) a memory bubble search [surprisingly faster than a linear search, yet still very slow given even a medium sized array] c) sorting account numbers [somewhat faster than a linear search but requiring constant re-sorts]. There are other methods as well, but needless to say, a hash function accomplishes this so simply it's hardly believable. [/COLOR][/COLOR]

---

### Post by ibuclaw on 2010-06-08
> **texaswriter said:**
> I wouldn't go out of your way to make speed improvements, especially if it ends up making your results inconsistent. Optimizations should be simple, where you know what the original code does and what exactly the replacement code will do, this way you can clearly be aware of any differences that will exist. 


Well, just one question to that then, will the amounts be an integer, or decimal number?

ie:
```
wd 1000 42
```
or
```
wd 1000 42.00
```
Knowing this will allow users to make the reasonable adjustments, rather than assuming one or the other.

---

### Post by texaswriter on 2010-06-08
[LEFT]I will use integer values, whole numbers. I will only do a brief test to see if overflow is trapped. That's all, the rest of the tests will be well within the bounds of a plain old integer. Use whatever type suits your programming style so long as only whole numbers are returned. 
[/LEFT]

---

### Post by pokebirdd on 2010-06-08
I don't really know much about hash tables, especially about how to avoid conflicts so I tried to use a binary tree which pretty much resizes to whatever amount of input you put in. I tested it with 10000 pieces of input and these are the times on my computer:
```
real    0m0.038s
user    0m0.032s
sys    0m0.004s

```Of course, if the account numbers were already presorted, this method would be no better (or probably worse than) a linear search. So I'll probably research a bit about how to get around this problem.

And here's the code for my program (not heavily commented):
```

#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <limits.h>
#define LINEMAX 100
#define CMD_WD 1
#define CMD_DEP 2
#define CMD_FEE 3

/* Structure containing each account, they'll be used in a binary tree */
struct account{
    int number;
    int balance;
    struct account *left;
    struct account *right;
};

/*  Reads a line (max n char including \n) from stdin and stores in s. 
 *  Returns pointer to s. To check if EOF is reached, check s[0]. */
char *readline(char *s, int n);

/* Reads at max nwords (max nchar) from source and stores the word in words.
 * Returns number of words read */
int getwords(char **words, char *source, int nwords, int nchar);

/* Recursive function to update the appropriate account, creating it if required */
struct account *addtree(struct account *head, int number, int balance, int cmd);

/* Prints out all the account balances, in order of their account number */
void print_tree(struct account *head);

/* Frees the memory allocated by the binary tree */
void free_tree(struct account *head);
            
int main(int argc, char *argv[]){
    int ii, nwords;
    int cmd, account_num, amount;
    struct account *head = NULL;
    char buf[LINEMAX];
    char **words = malloc(3 * sizeof(char *));
    for (ii = 0; ii < 3; ii++)
        words[ii] = malloc(LINEMAX);

    /*where all the real processing occurs*/
    while (readline(buf, LINEMAX)[0] != EOF){
        if (getwords(words, buf, 3, LINEMAX) != 3){
            printf("Error in line: \n%s", buf);
            continue; //don't process the line
        }
        /*parsing the 3 parts of a line. wish I could somehow use a switch statement*/
        if (!strcmp(words[0], "wd") || !strcmp(words[0], "cred"))
            cmd = CMD_WD;
        else if (!strcmp(words[0], "dep") || !strcmp(words[0], "deb"))
            cmd = CMD_DEP;
        else if (!strcmp(words[0], "fee"))
            cmd = CMD_FEE;
        else{
            printf("Unrecognized command: %s in line %s\n", words[0], buf);
            continue;
        }

        account_num = atoi(words[1]);
        amount = atoi(words[2]);
        head = addtree(head, account_num, amount, cmd);
    }
    print_tree(head);

    //free allocated memory
    free_tree(head);
    for (ii = 0; ii < 3; ii++)
        free(words[ii]);
    free(words);
}

char *readline(char *s, int n){
    int c, ii;
    for (ii = 0, c = 0; c != '\n' && c != EOF && ii < n - 1; ii++)
        s[ii] = c = getc(stdin);
    s[ii] = '\0';
    return s;
}

int getwords(char **words, char *source, int nwords, int nchar){
    int ii, jj; 
    for (ii = 0; ii < nwords && *source != '\0'; ii++){
        while (isspace(*source))
            source++;
        for (jj = 0; jj < nchar - 1 && !isspace(*source) && *source != '\0'; jj++)
            words[ii][jj] = *source++;
        //special case of whitespace before the '\0' char
        if (jj == 0 && *source == '\0')
            break;
        words[ii][jj] = '\0';
    }
    return ii;
}

/*These tree functions are pretty much taken out of K&R. But hey, I don't really
 *know how else you could implement a binary tree and the functions seemed elegant.*/
struct account *addtree(struct account *head, int number, int balance, int cmd){
    if (head == NULL){
        head = malloc(sizeof(struct account));
        head->number = number;
        head->balance = 0;
        head->left = NULL;
        head->right = NULL;
    }
    if (head->number == number){
        switch (cmd){
            case CMD_WD:
                /* no need to check for overflow, it never does */
                head->balance = head->balance - balance > 0 ? 
                head->balance - balance : 0;
                break;
            case CMD_DEP:
                if (head->balance + balance > INT_MAX)
                    head->balance += balance;
                else
                    printf("Operation not permitted: depositing too much money.\n");
                break;
            case CMD_FEE:
                if (head->balance - balance < INT_MIN)
                    head->balance -= balance;
                else
                    printf("Operation not permitted: charging too much money.\n");
                break;
            default:
                printf("Incorrect command code: %d\n", cmd);
                break;
        }
    }
    else if (head->number < number)
        head->left = addtree(head->left, number, balance, cmd);
    else
        head->right = addtree(head->right, number, balance, cmd);
    return head;
}

void print_tree(struct account *head){
    if (head != NULL){
        print_tree(head->left);
        printf("Number: %d; Balance: %d\n", head->number, head->balance);
        print_tree(head->right);
    }
}

void free_tree(struct account *head){
    if (head == NULL)
        return;
    free_tree(head->left);
    free_tree(head->right);
    free(head);
}

```

---

### Post by dv3500ea on 2010-06-08
@pokebirdd
Your program is by far the fastest, well done!
Just one thing - I think you have mixed up wd/cred with dep/deb.

---

### Post by pokebirdd on 2010-06-08
Thanks, I've corrected that. It's probably because I don't actually do any banking and stuff myself (I'm only still in high school :lolflag:). Anyways, I'll probably have to add some overflow checking; is there any other types of error checking I should do?

By the way, texaswriter, how exactly can do you judge the entries if some of them are written in a language you're unfamiliar with? Do you just give yourself a crash course on the syntax of the language? Or can you get other people to help you with the judging?

---

### Post by ibuclaw on 2010-06-08
> **pokebirdd said:**
> I don't really know much about hash tables, especially about how to avoid conflicts so I tried to use a binary tree which pretty much resizes to whatever amount of input you put in. I tested it with 10000 pieces of input and these are the times on my computer:
```
real    0m0.038s
user    0m0.032s
sys    0m0.004s

```

Oh woe! Beat me by **0.020** seconds! :KS

---

### Post by johnl on 2010-06-08
> **pokebirdd said:**
> Thanks, I've corrected that. It's probably because I don't actually do any banking and stuff myself (I'm only still in high school :lolflag:). Anyways, I'll probably have to add some overflow checking; is there any other types of error checking I should do?

By the way, texaswriter, how exactly can do you judge the entries if some of them are written in a language you're unfamiliar with? Do you just give yourself a crash course on the syntax of the language? Or can you get other people to help you with the judging?

It looks like your program leaks memory. Make sure to **free** any memory that you **malloc** when you no longer need it.

In this case it's probably not a big deal since the program will not run for long periods of time and the OS will release the memory when the program exits.

Edit:  if you want to see where you are allocating memory and forgetting to free it, you can run your program under **valgrind**:

```

ledbettj@reznor:~/Projects/test$ valgrind --leak-check=full ./test < test.txt
==27427== Memcheck, a memory error detector
==27427== Copyright (C) 2002-2009, and GNU GPL'd, by Julian Seward et al.
==27427== Using Valgrind-3.5.0-Debian and LibVEX; rerun with -h for copyright info
==27427== Command: ./test
==27427==
Number: 5; Balance: 0
Number: 4; Balance: 0
Number: 3; Balance: 1
Number: 2; Balance: 1
Number: 1; Balance: -1
==27427==
==27427== HEAP SUMMARY:
==27427==     in use at exit: 444 bytes in 9 blocks
==27427==   total heap usage: 9 allocs, 0 frees, 444 bytes allocated
==27427==
==27427== 120 (24 direct, 96 indirect) bytes in 1 blocks are definitely lost in loss record 5 of 7
==27427==    at 0x4C25153: malloc (vg_replace_malloc.c:195)
==27427==    by 0x400B2A: addtree (main.c:96)
==27427==    by 0x40094C: main (main.c:60)
==27427==
==27427== 324 (24 direct, 300 indirect) bytes in 1 blocks are definitely lost in loss record 7 of 7
==27427==    at 0x4C25153: malloc (vg_replace_malloc.c:195)
==27427==    by 0x400790: main (main.c:36)
==27427==
==27427== LEAK SUMMARY:
==27427==    definitely lost: 48 bytes in 2 blocks
==27427==    indirectly lost: 396 bytes in 7 blocks
==27427==      possibly lost: 0 bytes in 0 blocks
==27427==    still reachable: 0 bytes in 0 blocks
==27427==         suppressed: 0 bytes in 0 blocks
==27427==
==27427== For counts of detected and suppressed errors, rerun with: -v
==27427== ERROR SUMMARY: 2 errors from 2 contexts (suppressed: 4 from 4)

```

---

### Post by pokebirdd on 2010-06-09
I've fixed up my code so it frees the malloc'd memory. To be honest, I've never freed allocated memory in my programs thus far and there hasn't been a problem. After all, all the nodes in the tree are in use during the entire program and all the memory is automatically freed when the program ends right?

---

### Post by ibuclaw on 2010-06-09
> **pokebirdd said:**
> I've fixed up my code so it frees the malloc'd memory. To be honest, I've never freed allocated memory in my programs thus far and there hasn't been a problem. After all, all the nodes in the tree are in use during the entire program and all the memory is automatically freed when the program ends right?

Yes, but that still doesn't mean that you shouldn't get into the **good habit** of freeing memory that you malloc'd or calloc'd. Get it nailed early, and you'll be sailing down the line. :)

---

### Post by texaswriter on 2010-06-10
Pokebirdd> First question: Yeah, when I review the program, I basically google any terms I'm unfamiliar with. If I'm still lost, I'll message who coded it and asked. That's how I found out that those languages used hash keys. I saw where the account # was "searched" and it seemed that an undue amount of abstraction took place... So I figured either the language was doing some sort of search or a built-in hashing... 

But yeah, otherwise, if somebody uses an offbeat language, you can just say what language it's in. 

If I feel uncomfortable judging a program(s), I will enlist the help of somebody. In my life, I have programmed in BASIC, Pascal, C, a tiny bit C++. When you to higher-level languages, it doesn't usually get more complicated, usually just more abstracted. I bet most people who use the built-in hashing function aren't even aware of what the are doing besides just finding whatever member of their array they want as if magically.... and they are used to the magic... expect the magic. Implementing such magic in C requires specific coding. So, I recognized the abstraction immediately, being a C programmer, just wasn't entirely sure of what type of abstraction. Based on the speed, I thought it had to either be a really good search routine or a hashing routine.

Pokebirdd> Your program compiles and runs fast, however I'm not sure you have the transaction codes right. Double check the original post to ensure that the transaction codes are doing what they are supposed to. I'll retest yours when you've said you corrected this. 

Additionally, a blank line should terminate the program... I use this to test the times... Another thing, and it's largely your choice how to implement it. I need to test if the transaction codes are doing as they are supposed, so I need a way to check the balances. Either with each transaction print the new balance or print them at the end of the program [after input]... your choice... It would probably be better to print with each transaction. 

Also, for the code you got from K&R, that's fine for now. As an additional challenge after you've got the program working right you can implement it yourself, or perhaps try another approach. If you are up for the challenge. 

[B][COLOR=Red]Everybody else> Otherwise, I like everybody's entries, keep them rolling. Once again, I do want to mention, don't be daunted by the speed factor or by others code. If you write nice streamlined, modular code, it will be very easy to go back and change up one function if you decide later it can be much better. So, just start where things make sense to you and go from there. 
[/COLOR][/B]

---

### Post by pokebirdd on 2010-06-10
>  Pokebirdd> Your program compiles and runs fast, however I'm not sure  you have the transaction codes right. Double check the original post to  ensure that the transaction codes are doing what they are supposed to.  I'll retest yours when you've said you corrected this. I'm pretty sure the transaction codes were correct (wd = subtracting and dep = adding right?), but there I flipped the comparisons with INT_MAX and INT_MIN so it wasn't adding things properly.

Anyways, I've fixed that up and made it so that the account balance is printed after every line. Here's the fixed code:
```
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <limits.h>
#define LINEMAX 100
#define CMD_WD 1
#define CMD_DEP 2
#define CMD_FEE 3

/* Structure containing each account, they'll be used in a binary tree */
struct account{
    int number;
    int balance;
    struct account *left;
    struct account *right;
};

/*  Reads a line (max n char including \n) from stdin and stores in s. 
 *  Returns pointer to s. To check if EOF is reached, check s[0]. */
char *readline(char *s, int n);

/* Reads at max nwords (max nchar) from source and stores the word in words.
 * Returns number of words read */
int getwords(char **words, char *source, int nwords, int nchar);

/* Recursive function to update the appropriate account, creating it if required */
struct account *addtree(struct account *head, int number, int balance, int cmd);

/* Prints out all the account balances, in order of their account number */
void print_tree(struct account *head);

/* Returns the node with number n */
struct account *find_account(struct account *head, int n);

/* Frees the memory allocated by the binary tree */
void free_tree(struct account *head);
            
int main(int argc, char *argv[]){
    int ii, nwords;
    int cmd, account_num, amount;
    struct account *head = NULL;
    struct account *curr_node = NULL;
    char buf[LINEMAX];
    char **words = malloc(3 * sizeof(char *));
    for (ii = 0; ii < 3; ii++)
        words[ii] = malloc(LINEMAX);

    /*where all the real processing occurs*/
    while (readline(buf, LINEMAX)[0] != EOF){
        if (getwords(words, buf, 3, LINEMAX) != 3){
            printf("Error in line: \n%s", buf);
            exit(1);
        }
        /*parsing the 3 parts of a line. wish I could somehow use a switch statement*/
        if (!strcmp(words[0], "wd") || !strcmp(words[0], "cred"))
            cmd = CMD_WD;
        else if (!strcmp(words[0], "dep") || !strcmp(words[0], "deb"))
            cmd = CMD_DEP;
        else if (!strcmp(words[0], "fee"))
            cmd = CMD_FEE;
        else{
            printf("Unrecognized command: %s in line %s\n", words[0], buf);
            continue;
        }

        account_num = atoi(words[1]);
        amount = atoi(words[2]);
        head = addtree(head, account_num, amount, cmd);
        curr_node = find_account(head, account_num);
        printf("Account: %d, balance: %d\n", curr_node->number, curr_node->balance);
    }
    print_tree(head);

    //free allocated memory
    free_tree(head);
    for (ii = 0; ii < 3; ii++)
        free(words[ii]);
    free(words);
}

char *readline(char *s, int n){
    int c, ii;
    for (ii = 0, c = 0; c != '\n' && c != EOF && ii < n - 1; ii++)
        s[ii] = c = getc(stdin);
    s[ii] = '\0';
    return s;
}

int getwords(char **words, char *source, int nwords, int nchar){
    int ii, jj; 
    for (ii = 0; ii < nwords && *source != '\0'; ii++){
        while (isspace(*source))
            source++;
        for (jj = 0; jj < nchar - 1 && !isspace(*source) && *source != '\0'; jj++)
            words[ii][jj] = *source++;
        //special case of whitespace before the '\0' char
        if (jj == 0 && *source == '\0')
            break;
        words[ii][jj] = '\0';
    }
    return ii;
}

/*These tree functions are pretty much taken out of K&R. But hey, I don't really
 *know how else you could implement a binary tree and the functions seemed elegant.*/
struct account *addtree(struct account *head, int number, int balance, int cmd){
    if (head == NULL){
        head = malloc(sizeof(struct account));
        head->number = number;
        head->balance = 0;
        head->left = NULL;
        head->right = NULL;
    }
    if (head->number == number){
        switch (cmd){
            case CMD_WD:
                /* no need to check for overflow, it never does */
                head->balance = head->balance - balance > 0 ? 
                head->balance - balance : head->balance - 40;
                break;
            case CMD_DEP:
                if (head->balance + balance < INT_MAX)
                    head->balance += balance;
                else
                    printf("Operation not permitted: depositing too much money.\n");
                break;
            case CMD_FEE:
                if (head->balance - balance > INT_MIN)
                    head->balance -= balance;
                else
                    printf("Operation not permitted: charging too much money.\n");
                break;
            default:
                printf("Incorrect command code: %d\n", cmd);
                break;
        }
    }
    else if (head->number < number)
        head->left = addtree(head->left, number, balance, cmd);
    else
        head->right = addtree(head->right, number, balance, cmd);
    return head;
}

void print_tree(struct account *head){
    if (head != NULL){
        print_tree(head->left);
        printf("Number: %d; Balance: %d\n", head->number, head->balance);
        print_tree(head->right);
    }
}

struct account *find_account(struct account *head, int n){
    if (head->number == n)
        return head;
    else 
        return find_account(head->number > n ? head->right : head->left, n);
}
    

void free_tree(struct account *head){
    if (head == NULL)
        return;
    free_tree(head->left);
    free_tree(head->right);
    free(head);
}
```

---

### Post by texaswriter on 2010-06-10
Pokebirdd> You seemed to fix the problems previously, but now you have another problem. 

OK, If somebody makes what amounts to a withdrawal from an account [i.e. money coming out of the account], there has to be sufficient money for this. IF there is not sufficient money, the transaction is canceled and a fee is assessed [$40]. To be specific, if there is 100 in an account and I try to withdraw 1000, it should realize that that will over draw the account and *cancel* the transaction [and then assess a fee]. It seemed to me that the balance was going to zero arbitrarily when I tested that. 

Your program is not handling this properly. Why don't you try testing all the transaction codes to ensure they do the proper thing. 

Once again, let me know and I'll test.

---

### Post by schauerlich on 2010-06-10
> **texaswriter said:**
> IF there is not sufficient money, the transaction is canceled and a fee is assessed [$40].

Should I change my code so it charges $40 instead of $10?

---

### Post by texaswriter on 2010-06-11
> **schauerlich said:**
> Should I change my code so it charges $40 instead of $10?

If you want. I will actually assess each program separately to make sure what the final values should be from my large input file.... So, actually you don't even have to implement this fee at all if you don't want to. It is a minor issue... It would be nice though if everybody's programs did the same thing. 

Update: I'm switching my testing to a VM, just to cover myself. As such, any times will be greatly exaggerated from a real run-time expectation on a non-VM... But I will use the relative times. 

So, I am going to announce the one week time limit. Monday 11:59pm CST will be the *official* one-week deadline. So, that leaves about 10 days left in the competition. So far we've had a good number of challengers for the scale of the challenge. I'm personally of the opinion that it is well suited to get a beginner programmer using the languages in innovative ways. I leave it to people to either just satisfy the general requirements and not the technical. Or in other words, just make the program that accepts the input and maintains the list of accounts, updating them as necessary. Any way or method you do this is up to you. 

*Afterwards, if you still want more of a challenge, I highly encourage you try implementing your storage/retrieval method yourself. * 

Otherwise, good luck in the final 10 days. I hope to be posting updated comparison times to everybody's mailbox. ):P:KS

---

### Post by jim_24601 on 2010-06-11
> **texaswriter said:**
> I would recommend using a hashing technique

I don't think I would. Hash tables don't scale, and their worst case performance is bad. And coming up with a good hash function to avoid that worst case performance is hard, particularly since we don't know the distribution of account numbers in your data set.

In C++, I should unhesitatingly use a std::map, which is defined to have logarithmic worst-case performance, and probably uses a self-balancing binary tree, like a red-black tree. (A naive binary tree structure degenerates into a linked list if the keys are inserted in sorted order, so you've got linear performance again. Oops.)

> If you want extra credit

Don't you mean "extra debit"? :)

---

### Post by dv3500ea on 2010-06-11
> **texaswriter said:**
> Pokebirdd>
OK, If somebody makes what amounts to a withdrawal from an account [i.e. money coming out of the account], there has to be sufficient money for this. IF there is not sufficient money, the transaction is canceled and a fee is assessed [$40]. To be specific, if there is 100 in an account and I try to withdraw 1000, it should realize that that will over draw the account and *cancel* the transaction [and then assess a fee].

To clarify: 
If an account has a balance of 100 and something more is (attempted) withdrawn, should the new balance be 60? 
If an account has a balance of 20 and something more is (attempted) withdrawn should the new balance be -20?

---

### Post by texaswriter on 2010-06-12
> **jim_24601 said:**
> I don't think I would. Hash tables don't scale, and their worst case performance is bad. And coming up with a good hash function to avoid that worst case performance is hard, particularly since we don't know the distribution of account numbers in your data set.

In C++, I should unhesitatingly use a std::map, which is defined to have logarithmic worst-case performance, and probably uses a self-balancing binary tree, like a red-black tree. (A naive binary tree structure degenerates into a linked list if the keys are inserted in sorted order, so you've got linear performance again. Oops.)

Hrrm, hash keys are probably the most robust method of searching/storing entries that exists. Their worst performance is usually better than the average performance of alternatives. Coming up with a good hash function is as easy as finding a good hash key. Finding a good hash key is a matter of finding prime numbers. The nice thing about hash keys is IT WILL HANDLE any distribution of data, EVEN SORTED. I do believe random data is preferable, HOWEVER, by using prime numbers as the key, you can even handle regular data as well.  Data can be sequential [pre-sorted] as well and this doesn't even slow the hash function down. 

FWIW, hashing storage/retrieval [aka search time] is virtually zero given virtually any distribution of data. 

In C++, you can do std::hash as well I believe. Here is a link comparing the two, fwiw: [http://www.codeguru.com/forum/archive/index.php/t-386222.html](http://www.codeguru.com/forum/archive/index.php/t-386222.html)

As far as your other concern about scaling, if you base the prime key off of the size of the array [by some formula], than you can arbitrarily rehash every entry in the original hash table blindly into the new one and free() the original table. It's that simple. 


[COLOR=Red]For Beginners: [/COLOR]http://en.wikipedia.org/wiki/Hash_function will serve as a basic point of research. 
 



> **jim_24601 said:**
> Don't you mean "extra debit"? :)
:lolflag: Hah, yeah, thanks for catching that :-P

---

### Post by pokebirdd on 2010-06-12
> **texaswriter said:**
> Pokebirdd>
OK, If somebody makes what amounts to a withdrawal from an account [i.e. money coming out of the account], there has to be sufficient money for this. IF there is not sufficient money, the transaction is canceled and a fee is assessed [$40]. To be specific, if there is 100 in an account and I try to withdraw 1000, it should realize that that will over draw the account and *cancel* the transaction [and then assess a fee]. It seemed to me that the balance was going to zero arbitrarily when I tested that. 

Fixed.
Btw, could you upload a file with values for us to test AND the expected output for that file?

---

### Post by lisati on 2010-06-12
> **dv3500ea said:**
> To clarify: 
If an account has a balance of 100 and something more is (attempted) withdrawn, should the new balance be 60? 
If an account has a balance of 20 and something more is (attempted) withdrawn should the new balance be -20?

That's what sometimes happens in the real world, so why not?

---

### Post by dv3500ea on 2010-06-13
Here is my final program:

```
[color=#408080]*#!/usr/bin/env perl*[/color]
[color=#408080]*#*[/color]
[color=#408080]*#       challenge13.pl*[/color]
[color=#408080]*#       *[/color]
[color=#408080]*#       Copyright 2010*[/color]
[color=#408080]*#       *[/color]
[color=#408080]*#       This program is free software; you can redistribute it and/or modify*[/color]
[color=#408080]*#       it under the terms of the GNU General Public License as published by*[/color]
[color=#408080]*#       the Free Software Foundation; either version 2 of the License, or*[/color]
[color=#408080]*#       (at your option) any later version.*[/color]
[color=#408080]*#       *[/color]
[color=#408080]*#       This program is distributed in the hope that it will be useful,*[/color]
[color=#408080]*#       but WITHOUT ANY WARRANTY; without even the implied warranty of*[/color]
[color=#408080]*#       MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the*[/color]
[color=#408080]*#       GNU General Public License for more details.*[/color]
[color=#408080]*#       *[/color]
[color=#408080]*#       You should have received a copy of the GNU General Public License*[/color]
[color=#408080]*#       along with this program; if not, write to the Free Software*[/color]
[color=#408080]*#       Foundation, Inc., 51 Franklin Street, Fifth Floor, Boston,*[/color]
[color=#408080]*#       MA 02110-1301, USA.*[/color]

[color=#008000]**use**[/color] strict;
[color=#008000]**use**[/color] warnings;

[color=#408080]*#arguments:*[/color]
[color=#408080]*#only the first of '--speed' or '--debug' is processed*[/color]
[color=#408080]*#and only the first non-zero numerical argument is processed*[/color]
[color=#408080]*#if --speed is given, the results, unsorted, will be printed at the end of the program*[/color]
[color=#408080]*# and no warnings will be given.*[/color]
[color=#408080]*#if --debug is given, the balance after each transaction is printed, warnings are given*[/color]
[color=#408080]*# and the results are printed sorted at the end.*[/color]
[color=#408080]*#by default, the program runs the same as debug but without printing the balance*[/color]
[color=#408080]*# after each transaction.*[/color]
[color=#408080]*#the first non-zero argument will determine the overdraft fee, which defaults to 0*[/color]

[color=#008000]**my**[/color] [color=#19177C]$mode[/color] [color=#666666]=[/color] [color=#666666]2[/color];
[color=#008000]**my**[/color] [color=#19177C]$overdraft_fee[/color] [color=#666666]=[/color] [color=#666666]0[/color];[color=#408080]*#amount charged on overdraft*[/color]
[color=#008000]**foreach**[/color] ([color=#19177C]@ARGV[/color]) {
	[color=#008000]**if**[/color] ([color=#19177C]$_[/color] [color=#AA22FF]**eq**[/color] [color=#BA2121]'--debug'[/color] [color=#666666]&&[/color] [color=#19177C]$mode[/color] [color=#666666]==[/color] [color=#666666]2[/color]) {
		[color=#19177C]$mode[/color] [color=#666666]=[/color] [color=#666666]1[/color];
	} [color=#008000]**elsif**[/color] ([color=#19177C]$_[/color] [color=#AA22FF]**eq**[/color] [color=#BA2121]'--speed'[/color] [color=#666666]&&[/color] [color=#19177C]$mode[/color] [color=#666666]==[/color] [color=#666666]2[/color]) {
		[color=#19177C]$mode[/color] [color=#666666]=[/color] [color=#666666]0[/color];
	} [color=#008000]**elsif**[/color] ([color=#19177C]$overdraft_fee[/color] [color=#666666]==[/color] [color=#666666]0[/color]) {
		[color=#19177C]$overdraft_fee[/color] [color=#666666]=[/color] [color=#19177C]$_[/color][color=#666666]+[/color][color=#666666]0[/color];
	}
}

[color=#008000]**sub **[/color][color=#0000FF]mywarn[/color] {[color=#408080]*#warn unless --speed flag given*[/color]
	[color=#008000]**if**[/color] ([color=#19177C]$mode[/color]) {
		[color=#008000]warn[/color] [color=#19177C]$_[/color][[color=#666666]0[/color]];
	}
}

[color=#008000]**my**[/color] [color=#19177C]%accounts[/color] [color=#666666]=[/color] ();[color=#408080]*#hash for storing/retrieving accounts*[/color]

[color=#008000]**sub **[/color][color=#0000FF]dep[/color] { [color=#408080]*#function to deposit money into account*[/color]
		[color=#008000]**my**[/color] ([color=#19177C]$account[/color], [color=#19177C]$amount[/color]) [color=#666666]=[/color] [color=#19177C]@_[/color];[color=#408080]*#arguments - account_number, amount*[/color]
		[color=#008000]**if**[/color] ([color=#008000]exists[/color] [color=#19177C]$accounts[/color]{[color=#19177C]$account[/color]}) {[color=#408080]*#if account exists*[/color]
				[color=#19177C]$accounts[/color]{[color=#19177C]$account[/color]} [color=#666666]+=[/color] [color=#19177C]$amount[/color]; [color=#408080]*#add deposit amount to account balance*[/color]
		} [color=#008000]**else**[/color] {[color=#408080]*#if account doesn't exist*[/color]
				[color=#19177C]$accounts[/color]{[color=#19177C]$account[/color]} [color=#666666]=[/color] [color=#19177C]$amount[/color]; [color=#408080]*#create account with balance amount*[/color]
		}
		[color=#008000]**return**[/color] [color=#19177C]$accounts[/color]{[color=#19177C]$account[/color]}; [color=#408080]*#return new balance*[/color]
}

[color=#008000]**sub **[/color][color=#0000FF]fee[/color] { [color=#408080]*#function to charge a fee to the account*[/color]
		[color=#008000]**my**[/color] ([color=#19177C]$account[/color], [color=#19177C]$amount[/color]) [color=#666666]=[/color] [color=#19177C]@_[/color];[color=#408080]*#arguments - account_number, amount*[/color]
		[color=#008000]**if**[/color] ([color=#008000]exists[/color] [color=#19177C]$accounts[/color]{[color=#19177C]$account[/color]}) {[color=#408080]*#if account exists*[/color]
				[color=#19177C]$accounts[/color]{[color=#19177C]$account[/color]} [color=#666666]-=[/color] [color=#19177C]$amount[/color]; [color=#408080]*#take fee amount from account balance*[/color]
		} [color=#008000]**else**[/color] {[color=#408080]*#if account doesn't exist*[/color]
				mywarn [color=#BA2121]"What do you mean '$account', there is no such account!\n"[/color];
		}
		[color=#008000]**return**[/color] [color=#19177C]$accounts[/color]{[color=#19177C]$account[/color]}; [color=#408080]*#return new balance*[/color]
}

[color=#008000]**sub **[/color][color=#0000FF]wd[/color] { [color=#408080]*#function to withdraw from account*[/color]
		[color=#008000]**my**[/color] ([color=#19177C]$account[/color], [color=#19177C]$amount[/color]) [color=#666666]=[/color] [color=#19177C]@_[/color];[color=#408080]*#arguments - account_number, amount*[/color]
		[color=#008000]**if**[/color] ([color=#008000]exists[/color] [color=#19177C]$accounts[/color]{[color=#19177C]$account[/color]}) {[color=#408080]*#if account exists*[/color]
				[color=#008000]**if**[/color] ([color=#19177C]$accounts[/color]{[color=#19177C]$account[/color]} [color=#666666]>=[/color] [color=#19177C]$amount[/color]) {[color=#408080]*#only succeed if enough balance*[/color]
					[color=#19177C]$accounts[/color]{[color=#19177C]$account[/color]} [color=#666666]-=[/color] [color=#19177C]$amount[/color]; [color=#408080]*#take fee amount from account balance*[/color]
				} [color=#008000]**else**[/color] {
					mywarn [color=#BA2121]"You can't withdraw $amount if you only have $accounts{$account}, charging overdraft fee of $overdraft_fee!\n"[/color];
					fee([color=#19177C]$account[/color], [color=#19177C]$overdraft_fee[/color]);[color=#408080]*#charge the overdraft fee*[/color]
				}
		} [color=#008000]**else**[/color] {[color=#408080]*#if account doesn't exist*[/color]
				mywarn [color=#BA2121]"What do you mean '$account', there is no such account!\n"[/color];
		}
		[color=#008000]**return**[/color] [color=#19177C]$accounts[/color]{[color=#19177C]$account[/color]}; [color=#408080]*#return new balance	*[/color]
}

[color=#008000]**sub **[/color][color=#0000FF]parse[/color] {
		[color=#008000]**my**[/color] [color=#19177C]$str[/color] [color=#666666]=[/color] [color=#008000]shift[/color];
		[color=#008000]**my**[/color] ([color=#19177C]$trans[/color], [color=#19177C]$account[/color], [color=#19177C]$amount[/color]) [color=#666666]=[/color] [color=#008000]split[/color]([color=#BA2121]' '[/color], [color=#19177C]$str[/color]);
		[color=#408080]*#parse transaction_type account_num amount*[/color]
		[color=#19177C]$amount[/color] [color=#666666]+=[/color] [color=#666666]0[/color]; [color=#408080]*#turn amount into a number*[/color]
		[color=#19177C]$account[/color] [color=#666666]+=[/color] [color=#666666]0[/color]; 
		[color=#408080]*#ensure account is a number. This ensures numerical sorting of accounts as a opposed to alphabetical*[/color]
		[color=#008000]**if**[/color] ([color=#19177C]$trans[/color] [color=#AA22FF]**eq**[/color] [color=#BA2121]'wd'[/color] [color=#666666]||[/color] [color=#19177C]$trans[/color] [color=#AA22FF]**eq**[/color] [color=#BA2121]'cred'[/color]) {[color=#408080]*#withdraw commands*[/color]
				[color=#008000]**return**[/color] wd([color=#19177C]$account[/color], [color=#19177C]$amount[/color]);
		} [color=#008000]**elsif**[/color] ([color=#19177C]$trans[/color] [color=#AA22FF]**eq**[/color] [color=#BA2121]'fee'[/color]) {[color=#408080]*#fee command*[/color]
				[color=#008000]**return**[/color] fee([color=#19177C]$account[/color], [color=#19177C]$amount[/color]);
		} [color=#008000]**elsif**[/color] ([color=#19177C]$trans[/color] [color=#AA22FF]**eq**[/color] [color=#BA2121]'dep'[/color] [color=#666666]||[/color] [color=#19177C]$trans[/color] [color=#AA22FF]**eq**[/color] [color=#BA2121]'deb'[/color]) {[color=#408080]*#deposit commands*[/color]
				[color=#008000]**return**[/color] dep([color=#19177C]$account[/color], [color=#19177C]$amount[/color]);
		} [color=#008000]**else**[/color] {[color=#408080]*#mywarning on incorrect commands*[/color]
				mywarn [color=#BA2121]"'$trans' is not a transaction I understand! I do understand:\n
	dep or deb = where money is put in
	wd or cred = where money is taken out (as long as you have enough)
	fee = where money is taken out (even if you don't have enough)\n"[/color];
		} 
		[color=#008000]**return**[/color] [color=#BA2121]'0'[/color];
}

[color=#008000]**if**[/color] ([color=#19177C]$mode[/color] [color=#666666]==[/color] [color=#666666]1[/color]) {[color=#408080]*#debug*[/color]
	[color=#008000]**while**[/color] ([color=#666666]<[/color][color=#008000]STDIN[/color][color=#666666]>[/color]) {[color=#408080]*#loop over input*[/color]
		[color=#008000]**print**[/color] [color=#BA2121]"BALANCE: "[/color] [color=#666666].[/color] parse([color=#19177C]$_[/color]) [color=#666666].[/color] [color=#BA2121]"\n"[/color];[color=#408080]*#apply transactions and print new balance*[/color]
	} 
} [color=#008000]**else**[/color] {
	[color=#008000]**while**[/color] ([color=#666666]<[/color][color=#008000]STDIN[/color][color=#666666]>[/color]) {[color=#408080]*#loop over input*[/color]
		parse([color=#19177C]$_[/color]);
	} 
}

[color=#008000]**print**[/color] [color=#BA2121]"-"[/color] x [color=#666666]33[/color] [color=#666666].[/color] [color=#BA2121]"\n"[/color];

[color=#008000]**if**[/color] ([color=#19177C]$mode[/color]) {
		[color=#008000]**foreach**[/color] ([color=#008000]sort[/color] {[color=#19177C]$a[/color] [color=#666666]<=>[/color] [color=#19177C]$b[/color]} [color=#008000]keys[/color]([color=#19177C]%accounts[/color])) {
			[color=#008000]**print**[/color] [color=#BA2121]"Account: $_   Balance: $accounts{$_}\n"[/color];
		}
} [color=#008000]**else**[/color] {[color=#408080]*#speed*[/color]
		[color=#008000]**foreach**[/color] ([color=#008000]keys[/color]([color=#19177C]%accounts[/color])) {
			[color=#008000]**print**[/color] [color=#BA2121]"Account: $_   Balance: $accounts{$_}\n"[/color];
		}
}

```

It can be optimised for greater speed by passing an argument of '--speed'.
To see the balance after each transaction, pass '--debug' instead.
The amount charged on overdraft will be the first non-zero numerical argument. The default overdraft charge is 0, so you'll probably want to run the program with 40 as its 1st argument.

---

### Post by jim_24601 on 2010-06-14
> **texaswriter said:**
> Hrrm, hash keys are probably the most robust method of searching/storing entries that exists. Their worst performance is usually better than the average performance of alternatives.

I'm not an expert on hash tables, which is why I'd be wary of implementing my own. A naive implementation will degenerate into a list for pathological data (all values hash to the same bucket); you can get this down to O(log n) at the cost of added complexity. So worst case is comparable to a tree structure.

> Coming up with a good hash function is as easy as finding a good hash key. Finding a good hash key is a matter of finding prime numbers. The nice thing about hash keys is IT WILL HANDLE any distribution of data, EVEN SORTED. I do believe random data is preferable, HOWEVER, by using prime numbers as the key, you can even handle regular data as well.  Data can be sequential [pre-sorted] as well and this doesn't even slow the hash function down.

Again, I'm not an expert, but the Wikipedia page on "hash function" says that "the design of good hash functions is still a topic of active research", which isn't what I'd describe as "easy". Given the right hash function, you can get constant or near-constant insert and retrieval time, but without knowing how the keys are distributed I'd be hesitant to suggest one.

> In C++, you can do std::hash as well I believe.

It's a common extension, but not yet part of the standard.

> As far as your other concern about scaling, if you base the prime key off of the size of the array [by some formula], than you can arbitrarily rehash every entry in the original hash table blindly into the new one and free() the original table. It's that simple.

Of course you can, but then you've lost your linear insert time.

Now, I'm not dissing hash tables in general, and of course it's your challenge and you can specify it as you see fit. I'd still be inclined to go for an ordinary map (tree structure) in the first instance, and swap for a hash table only if I needed the extra speed and if I was confident I wouldn't hit any pathological cases and I could handle any resizing penalty.

---

### Post by texaswriter on 2010-06-14
> **jim_24601 said:**
> I'm not an expert on hash tables, which is why I'd be wary of implementing my own. A naive implementation will degenerate into a list for pathological data (all values hash to the same bucket); you can get this down to O(log n) at the cost of added complexity. So worst case is comparable to a tree structure.



Again, I'm not an expert, but the Wikipedia page on "hash function" says that "the design of good hash functions is still a topic of active research", which isn't what I'd describe as "easy". Given the right hash function, you can get constant or near-constant insert and retrieval time, but without knowing how the keys are distributed I'd be hesitant to suggest one.



It's a common extension, but not yet part of the standard.



Of course you can, but then you've lost your linear insert time.

Now, I'm not dissing hash tables in general, and of course it's your challenge and you can specify it as you see fit. I'd still be inclined to go for an ordinary map (tree structure) in the first instance, and swap for a hash table only if I needed the extra speed and if I was confident I wouldn't hit any pathological cases and I could handle any resizing penalty.

Great!! if you want to discuss it any further, take it to private email with me. Otherwise, I won't discuss it any further here. 

Here is the official one week notice. If somebody wants some more time to submit, don't feel shy asking for postponement. I will definitely postpone the end of the competition to accommodate more entries.

---

### Post by texaswriter on 2010-06-23
[B][COLOR=Red]Congratulations to all who participated!! Some interesting choices of languages and implementations were used. Very excited to have as many submissions. Although not a very hard challenge, I can appreciate that it appears daunting and therefore did not elicit as many programmers as it could. Even still, there were several that did submit programs and I applaud you all for your efforts. 

Hopefully, even if you didn't submit a program, the challenge got you to thinking about what it might have taken. 

Update: I looked over the programs and felt that two programmers in particular were newer programmers looking to flex their programming muscles. Congratulations to dv3500ea for your well-written program, motivation to try other methods of solving the problem, and otherwise stepping up to the challenge. Once again, congratulations to anybody who participated in this challenge as it proves you can take a step forward in this very challenging medium of programming. 

dv3500ea> I look forward to seeing your beginner programming challenge. Great job!!!


[/COLOR][/B]

---

### Post by dv3500ea on 2010-06-25
Thanks!

It was a fun challenge and made me think about how to optimise my program for speed, which I don't normally do.

I will post challenge 14 ASAP.

---

