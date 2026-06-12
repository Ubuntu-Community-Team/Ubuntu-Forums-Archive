---
title: "Thread to check and start program?"
date: 2005-11-29
forum: Programming Talk
---

### Post by lizardking on 2005-11-29
I have a litte big problem.
I made a **C/C++ mixing program.**I run it and it works.
 Then I put a while(1) in before a function beacuse **I want to relaunch that blocking function every times it finishes**. (the function is a **listener on a UDP** socket so is a blocking functions). The problem is that when I insert the loop the program at the second cycle of the loop goes in **Segmentation Fault**.
The function listen on a UDP socket than receive a string and to an iptables commmand throught this string.(I have adapter iptables-restore.c to do that)
Now I have debugged it with no result.
The program works perfectly without the while.
So I thought if I deleted the while and I made a main program that start **2 thread**:*one that execute the task and stop,other to check always the other thread and when it is finished it start the tread again and again..*
Some help on thread programming to do this?
:confused:

---

### Post by LordHunter317 on 2005-11-29
Better would be to post your code.  If it's segfaulting from adding a loop there is  a reason.  The threading solution almost assuredly won't work.

---

### Post by lizardking on 2005-11-29
OK I will try to put the essential code:
This is the C++ methods that **parse the command linea and call the execution of the operation**:
*To notice the while 1 in the down part of code*

*If  I cancel the while programs works well!If I leave the while : the firse cycle goes well the second segementation fault when do_iptables try to to inizialise the table with iptc_init(tablename)*

```

void Parser_d::parse() 			//PARSING
{
	isUp_struct param;							
	optind = 1;					// essenziale: altrimenti getopt funziona solo per il primo parser
	    int c;
		bool exec = false;
           while (1) {
              int option_index = 0;
               static struct option long_options[] = {
                   {"daemon",0,0,'d'},
                   {"ipman",1,0,0},
                   {"onport",0,0,0},
                   {0, 0, 0, 0}
               };
             c = getopt_long (arg_number, arguments, ":d0",
                        long_options, &option_index);
               if (c == -1)
                   break;

               switch (c) {
               case 0:
                    if (strncmp (long_options[option_index].name,"ipman",5) ==0) {
                    		          	param.ip=optarg;
                     }
                   if (strncmp (long_options[option_index].name,"onport",6) ==0) //disattivata , per ora è 40004
                   			param.port_to = atoi( optarg);
                   break;
              case 'd':
                   exec = true;
                    break;
               default:
               		{}

									                   
               }
           }
	bool par = false;
	param.port_to = 40004;
	par = oper ->setParam(  &param);		//se i parametri non sono validi deve ritornare false
	if (exec == true && par == true )	{
	while(1)	 oper ->execute();					// attiva il processo deamon che ascolta per le richieste del server e risponde
		
		}
}


```

This is the **body of oper->execute**: it's wait on the socket udp and than execut the do_iptables command who is the function riadapted of iptables-restore.c
```

void Operazione_ascolta::execute()			//attende un messaggio dal manager e ritorna la tabella di routing 
{
	printf ("Waiting for request... \n");
										/*
										 * quando gli risponde 
										 * stampa la risposta e invia la tabella di routing 
										 * in par -> ip c'e' l'ip del manager
										 * la porta su cui rispondere al manager è fissa: 40004
										 */
	 
	 
	 command_hdr *risposta;
	 risposta = (command_hdr *) pm->waitMessage (par->ip);
	 int cmd_id ;
	 int *l;
	 l = (int *)risposta;
	 int lenght = (*(l+1));
	 cmd_id = risposta->cmd_id;
	 unsigned char * query = new unsigned char (lenght);
	 unsigned char * tmp_payload = (unsigned char * )risposta ;
	 tmp_payload += sizeof ( command_hdr) ;    //point to the string payload
	 memcpy ( query, tmp_payload,lenght);
	 printf("%s", query);
	 
	 printf ("\nArrivata Richiesta: \ncmd_id = \t%d \nlenght = \t%d \npayload = \t%s\n", cmd_id, lenght ,query); 		/// è bloccante
	
	 int lun = strlen((const char *)query);
	 do_iptables(query, lun );


 char * mess = "iptables ricevuto";
 
 pm->setPayload((unsigned char *)mess,strlen(mess));
 pm->setHeader(2);
 pm->buildPacket();	//! cipher
 pm->send(par->ip,40004);
 }

```
Thi is the **code adaptdr from iptables-restore.c** to take a string and do the command:
```

void do_iptables(unsigned char * stringa, int lenght)
{
	iptc_handle_t handle = NULL;
	char buffer[10240];
	int c;
	char curtable[IPT_TABLE_MAXNAMELEN + 1];
	FILE *in;
	const char *modprobe = 0;
	int in_table = 0, testing = 0;

	program_name = "iptables-restore";
	program_version = IPTABLES_VERSION;
	line = 0;

	lib_dir = getenv("IPTABLES_LIB_DIR");
	if (!lib_dir)
		lib_dir = IPT_LIB_DIR;



   const char * s = getString(stringa , lenght);
   printf("stringa da  passare a iptabels resotre= %s",s);
   printf("\n");



				
		char * table = "filter";
		strncpy(curtable, table, IPT_TABLE_MAXNAMELEN);
		curtable[IPT_TABLE_MAXNAMELEN] = '\0';
		if (handle)
				iptc_free(&handle);

		handle = create_handle(table, modprobe);
		int ret = 1;
		in_table = 1;

			int a;
		        char *ptr = s;
			char *pcnt = NULL;
			char *bcnt = NULL;
			char *parsestart;

			/* the parser */
			 char *param_start, *curchar;
			int quote_open;

			/* reset the newargv */
			newargc = 0;


				/* start command parsing at start of line */
				parsestart = s;
			

			add_argv("./iptables-restore");
			add_argv("-t");
			add_argv((char *) &curtable);


			/* After fighting with strtok enough, here's now
			 * a 'real' parser. According to Rusty I'm now no
			 * longer a real hacker, but I can live with that */

			quote_open = 0;
			param_start = parsestart;
			
			for (curchar = parsestart; *curchar; curchar++) {
				if (*curchar == '"') {
					/* quote_open cannot be true if there
					 * was no previous character.  Thus, 
					 * curchar-1 has to be within bounds */
					if (quote_open && 
					    *(curchar-1) != '\\') {
						quote_open = 0;
						*curchar = ' ';
					} else {
						quote_open = 1;
						param_start++;
					}
				} 
				if (*curchar == ' '
				    || *curchar == '\t'
				    || * curchar == '\n') {
					char param_buffer[1024];
					int param_len = curchar-param_start;

					if (quote_open)
						continue;

					if (!param_len) {
						/* two spaces? */
						param_start++;
						continue;
					}
					
					/* end of one parameter */
					strncpy(param_buffer, param_start,
						param_len);
					*(param_buffer+param_len) = '\0';

					/* check if table name specified */
					if (!strncmp(param_buffer, "-t", 3)
                                            || !strncmp(param_buffer, "--table", 8)) {
						exit_error(PARAMETER_PROBLEM, 
						   "Line %u seems to have a "
						   "-t table option.\n", line);
						exit(1);
					}

			
                    			
						add_argv(param_buffer);
					
					param_start += param_len + 1;
				} else {
					/* regular character, skip */
				}
			}

		

			

			ret = do_command(newargc, newargv, 
					 &newargv[2], &handle);

			free_argv();
			ret = iptc_commit(&handle);



}



```

---

### Post by LordHunter317 on 2005-11-29
I'm not confident how that code works at all.  At any rate, I'm pretty sure when you do the pointer math on tmp_payload to move it to the payload, you're walking off the end of the world.

What type is command_hdr?  If it's a struct, dereference it correctly.  If it's not, it ought to be.

And stop leaking memory.

---

### Post by lizardking on 2005-11-29
[QUOTE=LordHunter317]I'm pretty sure when you do the pointer math on tmp_payload to move it to the payload, you're walking off the end of the world.[/QUOTE]
What do you mean?
[QUOTE=LordHunter317]
What type is command_hdr?  If it's a struct, dereference it correctly.  If it's not, it ought to be.

And stop leaking memory.[/QUOTE]
Command_hdr is a struct that contains 2 int with attributed packed

---

### Post by LordHunter317 on 2005-11-29
> **lizardking]What do you mean?[/quote]This line:[quote]```
 tmp_payload += sizeof ( command_hdr)  said:**
> Is likely pointing at something you don't think it is, and causing the SIGSEGV.

You're getting lucky that it's working the first time, bascially.
[quote]Command_hdr is a struct that contains 2 int with attributed packedThen your code above is certainly semantically illegal, to say the least.

---

### Post by lizardking on 2005-11-30
[QUOTE=LordHunter317]This line:Is likely pointing at something you don't think it is, and causing the SIGSEGV[/QUOTE]
:confused:  It's not here that the program goes in SIGSV but when calls iptc_init() in do_itpables

---

### Post by LordHunter317 on 2005-11-30
Maybe I'm missing something, but I don't see that call in any of the code you posted.  

At any rate, your code contains numberous bugs and some dangerous pointer math.  You should rewrite most of it anyway, even if it's not related to this issue.

Anyway, my new WAG is that you're leaking handles to the filter table, you never call iptc_free on your handle at the end of the function.

---

### Post by Roptaty on 2005-12-01
```
unsigned char * query = new unsigned char (lenght) 
```
This one is baaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaad. 

Parenthesis are not the same as square brackets []. You are actually only allocating ONE unsigned char here which will be initialized to the value lenght. 

The "funny" thing about overwriting memory and getting SIGSEGVs is that the SIGSEGVs do not normally occur where you are overwriting the memory. A good tool to check if you are overwriting/allocating/freeing memory is valgrind. Use it.

---

### Post by thumper on 2005-12-01
[QUOTE=LordHunter317]Anyway, my new WAG is that you're leaking handles to the filter table, you never call iptc_free on your handle at the end of the function.[/QUOTE]
What's a WAG?

---

### Post by LordHunter317 on 2005-12-01
Wild-Ass Guess.

It's possible that's it, it's possible it's something else.  There's so much bad pointer code there's no real way to tell.

I second the valgrind recommendation and sorta slap myself for not making it first.

Though, most of that code needs to be rewritten anyway, so it's sorta moot, I suppose.

---

