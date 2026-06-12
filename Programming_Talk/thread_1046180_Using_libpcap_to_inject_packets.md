---
title: "Using libpcap to inject packets"
date: 2009-01-21
forum: Programming Talk
---

### Post by dinopeso on 2009-01-21
im trying to inject some bytes on tcp/ip stack. im using some methods of libpcap.h

int pcap_sendpacket(pcap_t *p, const u_char *buf, int size);

this methods returns 0 on success and -1 on failure.

i dont know how to test my aplication.

could anyone help?

---

### Post by dinopeso on 2009-01-21
does anyone can tell me if me code is correct or not ?

#include <stdio.h>
#include <pcap.h>

int main(int argc, char *argv[])
{
	char * testeArray = "Danilo Assis";
	char *dev; 			/* Network Device(s) driver */
	char errbuf[PCAP_ERRBUF_SIZE];
	pcap_t *descr;   		/* Session(s) description   */
	void *contents = NULL;		/* Data to inject           */
	int i = 0;

	if (getuid()) 
	{
        	printf("Error! Must be root ... exiting\n");
        	return (1);
  	}


	dev = pcap_lookupdev(errbuf);
	
	if (dev == NULL) 
	{
		fprintf(stderr, "Couldn't find default device: %s\n", errbuf);
		return(2);
	}
	printf("Device: %s\n", dev);
 		
	/* Set the pcap description */
	descr = pcap_open_live(dev, BUFSIZ, 1, 0, errbuf);
	
	if (descr == NULL)
	{
        	printf("pcap_open_live(): %s\n", errbuf);
        	return (1);
  	}
	/* Here we loop the injector */
	int flag_retorno = 1;

    	for (; i <= 20; i++) {
        /*if (vflag)*/
        	flag_retorno = pcap_sendpacket (descr,testeArray, sizeof(testeArray));

		if(flag_retorno == 0)
		{
			printf("Injecting packet on %s: 1 second delay\n",dev);
        		sleep(1);
		}
    	}

	return(0);
}

---

### Post by dinopeso on 2009-02-16
i created this topic last month but nobody answered it. does anybody could help ?

---

### Post by dinopeso on 2009-02-17
all i want to do is inject ip packets on eth0. here below im going to put what i want to inject and my code.

dev = pcap_lookupdev(errbuf);
descr = pcap_open_live(dev, BUFSIZ, 1, 0, errbuf);
int bytesInjetados = 0;
bytesInjetados = pcap_inject(descr,payload, sizeof(payload));

this method pcap_inject() is always returning the number 4 and i dont know why.

payload is what i want to inject and this array has it: 

Printing payload
45 
0 5 40 2d 72 40 0 40 11 a 39 7f 0 0 1 7f 0 0 1 b3 da 30 39 5 2c 
3 40 47 20 11 1d 6 83 b8 6a 19 63 57 e3 4c d5 50 0 0 1c b2 31 ad 6b 5a 
d6 a9 a8 19 7 41 ad 69 20 73 0 20 90 b 50 c4 b0 45 8b 1f cc 92 bb b3 11 
fe 86 2f ee c3 24 18 b4 48 df 7b a5 b0 70 37 e8 27 e8 f9 df f6 f4 51 41 d8 
c0 e3 7f b7 73 9e 16 f4 7b 52 ad 3c 7f e6 8e e7 3a e9 48 a9 c6 f5 e9 e7 a4 
32 f f0 17 19 56 7f 48 da 9 48 43 29 f3 f8 8c 79 6c d9 79 82 3f e8 45 98 
59 62 3f a0 20 cd f 6a b8 1a 55 fb aa 1 33 3b 6 83 4b 3 9d 4b 5a f2 cf 
71 4d ba aa 5c 79 88 98 2a f7 94 f5 1f 5c c8 9b 1d 99 bf c7 88 38 ef 82 6d 
a7 9f ce 76 56 4 f0 80 70 27 77 d3 59 88 5f 47 60 11 1e 0 0 1 bd 5 ba 
83 80 5 27 86 97 5c bb 3f 53 a9 1e 50 b5 be c4 3f f0 23 5e a1 8f 3d ed 41 
8c f f9 cd b0 ff 4b 11 ed aa d0 78 f0 12 10 58 52 b0 f3 6a 77 13 95 fc 6b 
93 d0 2f 39 99 b1 5f 98 9d b df dd 3 24 18 b9 23 ef 79 6c e 7 f4 f d1 
f9 c0 0 0 3e 5a 73 6e 96 c0 a8 6e 5c b6 d 6b 94 d6 b8 e0 94 c2 b 77 36 
57 1c 30 4b 7f 53 80 1 0 0 7e 9b eb 86 a e9 f5 7a ea 2c 53 1b 36 51 26 
9c 13 33 e4 99 f4 e5 68 29 3a 85 bd 33 8e 77 12 af 54 96 13 a7 4f dd 3e 7e 
e9 cc 77 d4 ab 3e 7c fd 53 b7 30 a1 bf 4c 99 53 d7 ca d2 dc bd 4a b3 f7 4e 
6c 25 8c 47 20 11 1f 2b a7 d5 eb fc f9 19 53 a8 6f d4 d6 ae e2 c3 e7 cf 77 
ba 5c ba 95 71 b3 62 29 cd a 93 f5 43 21 be 86 96 bd 1a d0 d4 c3 ab a 22 
4a 54 d4 c3 4c 86 14 2d ce 54 be e8 86 f1 61 2a 9f 15 7d 21 f1 97 f6 e2 44 
37 da 13 5 ea e8 8a c9 f0 c0 2a c0 1b 55 f8 76 5b df ca de eb a3 e5 8f cb 
c4 8f 60 e 60 8f 96 9a df c5 eb 51 7b 25 82 1 7 6a 98 d0 1b 91 6e 3d f4 
8e 7f a7 78 dc 35 b4 66 63 1 60 d0 31 c1 f8 b1 f 34 f4 ac b7 da 3e 95 72 
ac b8 c1 fc a7 19 7d 8 0 17 7b 84 ad 51 b 25 c5 29 29 60 6a f9 5b a1 7f 
e0 b 76 5a 36 c0 5f 99 37 eb af d8 6 f9 22 13 47 20 11 10 fe b8 6 76 96 
85 cb e3 e4 45 96 a2 8d 70 8b be 6d 4f a3 e3 11 5f be 26 41 13 5 fe 23 d6 
54 21 f e6 c6 fc 83 e4 c2 3 9c 1c 96 ae dc 8d df 77 53 68 e8 5c c2 98 b2 
28 7 b1 3 70 44 52 57 e0 26 d9 37 94 2f b2 48 f4 2 7 bb 7d a1 30 5e ae 
88 ac 9f c 2 ac 1 b5 5f 87 65 bd fc 0 0 f 1c b2 b6 cd b3 b2 35 54 98 
48 2d ad 6b 82 d5 30 c0 0 c3 a0 c0 eb 39 1b b0 3a 8 ec 6e 8a 11 bc e6 8a 
3d 58 21 e6 9b ca 30 f1 36 51 f5 11 9d f6 df 31 35 cf c2 5f 2a 8b 10 17 62 
3 ea c 94 76 c4 da 81 72 13 4e 8b 78 4f 54 a2 35 dd 7b 1 f2 d0 5b 11 fc 
80 99 9e 98 47 20 11 11 1a e9 d 55 6b f9 61 cc 1 7c 4d 6e 13 e2 3 0 c 
af 62 23 2f a3 a6 19 cd f3 da d1 c2 fa c1 99 1f c6 3f bf 9 52 15 8a c6 83 
c3 7c e4 48 2 82 a3 7b 54 44 4d 14 42 62 ed 19 f 4a f3 fb d1 b5 91 7e 12 
2 40 28 1b 40 a2 0 f9 87 fe e0 62 cc 38 ce 91 75 c1 6e f4 ca 82 b4 6 3f 
ba 3a 8e 9d b1 a7 4e d5 c5 a8 36 9f 62 e0 e4 17 4a e8 47 82 6e c7 15 95 8e 
92 fd c6 8c 3a c e b3 91 bb 3 a0 8e c6 e8 a1 1b ce 68 a3 d5 80 0 1 e5 
c6 96 da cd 23 6d 35 53 1c d6 e9 84 6a af 66 98 0 c9 c4 8 33 71 3e b5 cf 
d8 d3 bd b0 e e 55 b4 c8 a8 d6 84 1c fe 79 ee d6 47 0 10 3c 11 0 ff ff 
ff ff ff ff ff ff ff ff ff ff ff ff ff ff b6 76 8d 2b 5a d2 35 71 ff 14 d1 
8a 35 4d 1a 56 b3 6a ef ba 69 89 a4 24 d2 b 4c 2d 21 b4 c6 bd 95 68 d7 87 
54 91 b7 a7 af bc e8 6f a0 63 ff fa fb a6 f5 d1 be 81 8c 0 66 f9 13 ae 34 
8f d3 3e 9e ba 27 8b 13 a3 ea 4f aa be b9 3e fa fa 1f 5f 5d 7d 75 eb 7a fa 
e6 fb 23 4d f7 d3 44 e4 9f c5 5d 5d f2 ae 4f a3 a6 fb a1 3e 82 eb ec da f4 
ae 6f aa 4f ba b 1f f1 5f c9 a7 93 67 68 d9 9b 5a d2 35 77 af 93 e9 52 7a 
57 5e 44 e8 ea fa 3a 6f a1 f0 0 0 1 44 2a b0 10 2 0 40 26 fb 68 0 0 
0 0 0 0 0 47 40 10 1d 0 0 1 e0 0 0 87 c0 a 37 86 9b 76 ef 17 86 
9b 3c 47 0 0 1 0 2c cf ff f8 0 0 1 b5 8f ff fb db 80 0 0 0 0 0 
1 1 5b fe 3a 70 3 87 2 38 1 e1 9 b9 8d d4 e0 7 e 4 70 3 c2 13 72 
1b 91 bd 1a dd 8c 5a a6 b1 93 5b 61 83 16 56 4c 9b b1 a3 6 8c 9a db 8d 1a 
31 6a 64 d8 62 cc c1 a1 9b 61 99 83 6 b6 4d b3 16 46 b1 a1 93 6a d1 99 a3 
53 d ab 6 76 8c 30 da b4 66 68 c9 86 d1 95 9d 91 86 1b 2d 19 58 35 30 db 
35 6d 63 2b 26 4d bb 2b 16 8c d9 b6 8c 1a c6 c d8 6d 59 da 31 64 c3 68 d1 
8b 46 18 6c b1 6a d9 d9 b0 da 33 32 b0 64 d2 d8 6b 1a 


much bigger than 4. does anyone know what is happening?

---

### Post by Kishwar on 2010-01-21
Hi Dinopeso,
Can you please share whether you had been able to use pcap_inject() function properly? 
I also need to inject packets to an interface after reading it from another interface.
Regards,
Kishwar.

---

