---
title: "can't compile cpp programming"
date: 2009-03-05
forum: Programming Talk
---

### Post by AlexenderReez on 2009-03-05
main.cpp
[PHP]#include <iostream.h>

#include <stdlib.h>

#include <string.h>



#include "DES.h"



char* Convert2Bin(char[]);

char* Binary(char);

void InsertInArray(char*,char[]);

char* Convert2Hex(char*);

char Hexa(char,char,char,char);



void main()

{

	char ed;

	char *data = new char[DATA_LENGTH];

	char *key = new char[KEY_TOTAL_LENGTH];

	data[0] = '\0';

	key[0] = '\0';



	char *tData = new char[64];

	char *tKey = new char[64];



	cout << endl << "Encryption/Decryption? E/D: ";

	cin >> ed;



	if (tolower(ed) == 'e')

	{

		//perform encryption

		cout << endl << "Starting Encryption..." << endl;



		cout << endl << "Enter Data to encrypt: ";

		cin >> tData;

		cout << endl << "Enter Encryption Key: ";

		cin >> tKey;



#ifdef SDES

		strcpy(data,tData);

		strcpy(key,tKey);

#else

		strcpy(data,Convert2Bin(tData));

		strcpy(key,Convert2Bin(tKey));

#endif

		CDES *des = new CDES(data,key);

		char* cipher = des->Encrypt();



#ifdef DES

		cipher = Convert2Hex(cipher);

#endif



		cout << endl << "Encrypted Text: " << cipher << endl;

	}

	else if (tolower(ed) == 'd')

	{

		//perform decryption

		cout << endl << "Starting Decryption..." << endl;



		cout << endl << "Enter Data to Decrypt: ";

		cin >> tData;

		cout << endl << "Enter Decryption Key: ";

		cin >> tKey;



#ifdef SDES

		strcpy(data,tData);

		strcpy(key,tKey);

#else

		strcpy(data,Convert2Bin(tData));

		strcpy(key,Convert2Bin(tKey));

#endif

		CDES *des = new CDES(data,key);

		char *plain = des->Decrypt();



#ifdef DES

		plain = Convert2Hex(plain);

#endif



		cout << endl << "Decrypted Text: " << plain << endl;

	}

	else

	{

		//invalid choice... neither e nor d

		cout << endl << "We support only e and d..." << endl;

	}

}



char* Convert2Hex(char* out)

{

	int i,j;

	char hexchar;

	char *put = new char[DATA_LENGTH/4];



	for (i = 0,j = 0 ; i < DATA_LENGTH ; j++, i += 4)

	{

		hexchar = Hexa(out[i],out[i+1],out[i+2],out[i+3]);

		put[j] = hexchar;

	}



	put[j] = '\0';



	return put;

}



char Hexa(char a, char b, char c, char d)

{

	if		(a == '0' && b == '0' && c == '0' && d == '0')

		return '0';

	else if (a == '0' && b == '0' && c == '0' && d == '1')

		return '1';

	else if (a == '0' && b == '0' && c == '1' && d == '0')

		return '2';

	else if (a == '0' && b == '0' && c == '1' && d == '1')

		return '3';

	else if (a == '0' && b == '1' && c == '0' && d == '0')

		return '4';

	else if (a == '0' && b == '1' && c == '0' && d == '1')

		return '5';

	else if (a == '0' && b == '1' && c == '1' && d == '0')

		return '6';

	else if (a == '0' && b == '1' && c == '1' && d == '1')

		return '7';

	else if (a == '1' && b == '0' && c == '0' && d == '0')

		return '8';

	else if (a == '1' && b == '0' && c == '0' && d == '1')

		return '9';

	else if (a == '1' && b == '0' && c == '1' && d == '0')

		return 'A';

	else if (a == '1' && b == '0' && c == '1' && d == '1')

		return 'B';

	else if (a == '1' && b == '1' && c == '0' && d == '0')

		return 'C';

	else if (a == '1' && b == '1' && c == '0' && d == '1')

		return 'D';

	else if (a == '1' && b == '1' && c == '1' && d == '0')

		return 'E';

	else

		return 'F';

}



char* Convert2Bin(char data[])

{

	unsigned int i;

	char *bins;

	char *array = new char[DATA_LENGTH];

	array[0] = '\0';



//	cout << endl << "Data to Convert : " << data;



	for (i = 0 ; i < strlen(data) ; i++)

	{

		bins = Binary(data[i]);

//		cout << endl << bins;

		InsertInArray(bins,array);

//		cout << endl << "Array : " << array;

	}



	return array;

}



void InsertInArray(char* b,char* arr)

{

	int i,j;



	for (i = strlen(arr),j = 0 ; j < 4 ; i++,j++)

	{

		arr[i] = b[j];

	}



	arr[i] = '\0';

}



char* Binary(char c)

{

	switch(c)

	{

	case '0':

		return "0000";

	case '1':

		return "0001";

	case '2':

		return "0010";

	case '3':

		return "0011";

	case '4':

		return "0100";

	case '5':

		return "0101";

	case '6':

		return "0110";

	case '7':

		return "0111";

	case '8':

		return "1000";

	case '9':

		return "1001";

	case 'A':

		return "1010";

	case 'B':

		return "1011";

	case 'C':

		return "1100";

	case 'D':

		return "1101";

	case 'E':

		return "1110";

	case 'F':

		return "1111";

	default:

		return "";

	}

}[/PHP]

des.cpp
[PHP]// DES.cpp: implementation of the CDES class.

//

//////////////////////////////////////////////////////////////////////

#include <iostream.h>

#include <string.h>

#include <stdlib.h>



#include "DES.h"



//////////////////////////////////////////////////////////////////////

// Construction/Destruction

//////////////////////////////////////////////////////////////////////



CDES::CDES(char* data, char* key)

{

	strcpy(this->data,data);

	this->data[strlen(this->data)] = '\0';

	strcpy(this->Compkey,key);

	this->Compkey[strlen(this->Compkey)] = '\0';



	cout << endl << "DATA:";

	print(this->data,DATA_LENGTH);

	cout << endl << "KEY:";

	print(this->Compkey,KEY_TOTAL_LENGTH);



	FillAllS();

//	SampleKeys();

}



CDES::~CDES()

{



}



char* CDES::Encrypt()

{

	// Calculate Keys

	GenKeys();



	// Begin Encryption

#ifdef SDES

	char *ip = DataIP(); // Initial Permutation on Input bits

#else

	char *ip = DataIP_DES();

#endif



	cout << endl << "Initial Permutation";

	print(ip,DATA_LENGTH);



	char *loopData = ip;

	char *FKr;



	for (int i = 1 ; i <= NO_OF_KEYS ; i++)

	{

		FKr = FKFunction(loopData,i);



		cout << endl << "FK" << i << " Result";

		print(FKr,DATA_LENGTH);



		if (i != NO_OF_KEYS)

		{

			loopData = Switch(FKr);

			

			cout << endl << "Switch Result";

			print(loopData,DATA_LENGTH);

		}

		else

		{

			loopData = FKr;

		}

	}



	char *IPinv = IPInverse(loopData);



	cout << endl << "IP Inverse";

	print(IPinv,DATA_LENGTH);



	return IPinv;

}



char* CDES::keyIPermutation()

{

#ifdef SDES

	char *keyP = new char[KEY_TOTAL_LENGTH];



	keyP[0] = Compkey[3-1];

	keyP[1] = Compkey[5-1];

	keyP[2] = Compkey[2-1];

	keyP[3] = Compkey[7-1];

	keyP[4] = Compkey[4-1];

	keyP[5] = Compkey[10-1];

	keyP[6] = Compkey[1-1];

	keyP[7] = Compkey[9-1];

	keyP[8] = Compkey[8-1];

	keyP[9] = Compkey[6-1];

#else

	char *keyP = new char[KEY_USED_BITS];



	keyP[0] = Compkey[57-1];

	keyP[1] = Compkey[49-1];

	keyP[2] = Compkey[41-1];

	keyP[3] = Compkey[33-1];

	keyP[4] = Compkey[25-1];

	keyP[5] = Compkey[17-1];

	keyP[6] = Compkey[9-1];

	keyP[7] = Compkey[1-1];

	keyP[8] = Compkey[58-1];

	keyP[9] = Compkey[50-1];

	keyP[10] = Compkey[42-1];

	keyP[11] = Compkey[34-1];

	keyP[12] = Compkey[26-1];

	keyP[13] = Compkey[18-1];

	keyP[14] = Compkey[10-1];

	keyP[15] = Compkey[2-1];

	keyP[16] = Compkey[59-1];

	keyP[17] = Compkey[51-1];

	keyP[18] = Compkey[43-1];

	keyP[19] = Compkey[35-1];

	keyP[20] = Compkey[27-1];

	keyP[21] = Compkey[19-1];

	keyP[22] = Compkey[11-1];

	keyP[23] = Compkey[3-1];

	keyP[24] = Compkey[60-1];

	keyP[25] = Compkey[52-1];

	keyP[26] = Compkey[44-1];

	keyP[27] = Compkey[36-1];

	keyP[28] = Compkey[63-1];

	keyP[29] = Compkey[55-1];

	keyP[30] = Compkey[47-1];

	keyP[31] = Compkey[39-1];

	keyP[32] = Compkey[31-1];

	keyP[33] = Compkey[23-1];

	keyP[34] = Compkey[15-1];

	keyP[35] = Compkey[7-1];

	keyP[36] = Compkey[62-1];

	keyP[37] = Compkey[54-1];

	keyP[38] = Compkey[46-1];

	keyP[39] = Compkey[38-1];

	keyP[40] = Compkey[30-1];

	keyP[41] = Compkey[22-1];

	keyP[42] = Compkey[14-1];

	keyP[43] = Compkey[6-1];

	keyP[44] = Compkey[61-1];

	keyP[45] = Compkey[53-1];

	keyP[46] = Compkey[45-1];

	keyP[47] = Compkey[37-1];

	keyP[48] = Compkey[29-1];

	keyP[49] = Compkey[21-1];

	keyP[50] = Compkey[13-1];

	keyP[51] = Compkey[5-1];

	keyP[52] = Compkey[28-1];

	keyP[53] = Compkey[20-1];

	keyP[54] = Compkey[12-1];

	keyP[55] = Compkey[4-1];

#endif



	return keyP;

}



char* CDES::LeftShift(char *keyPF, char LorR, int bits)

{

	char *sbits = new char[KEY_USED_BITS/2];

	int i,k;



	if (LorR == 'L')		// shift left bits

	{

		for (i = 0,k = 0 ; i < (KEY_USED_BITS/2) ; i++,k++)

		{

			sbits[i] = keyPF[k];

		}

	}

	else if (LorR == 'R')	// shift right bits

	{

		for (i = 0,k = (KEY_USED_BITS/2) ; i < (KEY_USED_BITS/2) ; i++,k++)

		{

			sbits[i] = keyPF[k];

		}

	}



	char temb;



	// Shift the Bits

	for (i = 1 ; i <= bits ; i++)

	{

		temb = sbits[(KEY_USED_BITS/2)-1];

		for (int k = 0 ; k < (KEY_USED_BITS/2) ; k++)

		{

			if ((KEY_USED_BITS/2)-1 == k)

				sbits[(k+((KEY_USED_BITS/2)-1)) % (KEY_USED_BITS/2)] = temb;

			else

				sbits[(k+((KEY_USED_BITS/2)-1)) % (KEY_USED_BITS/2)] = sbits[k];

		}

	}



	return sbits;

}



char* CDES::JoinShifted(char *Lbits, char *Rbits)

{

	char *key1 = new char[KEY_USED_BITS];



	int i,j;



	for (i = 0 ; i < (KEY_USED_BITS/2) ; i++)

	{

		key1[i] = Lbits[i];

	}



	for (i = (KEY_USED_BITS/2),j = 0 ; j < (KEY_USED_BITS/2) ; i++,j++)

	{

		key1[i] = Rbits[j];

	}



	return key1;

}



void CDES::keyPermutationA(char *keyJoined,int k)

{

#ifdef SDES

	key[k-1][0] = keyJoined[6-1];

	key[k-1][1] = keyJoined[3-1];

	key[k-1][2] = keyJoined[7-1];

	key[k-1][3] = keyJoined[4-1];

	key[k-1][4] = keyJoined[8-1];

	key[k-1][5] = keyJoined[5-1];

	key[k-1][6] = keyJoined[10-1];

	key[k-1][7] = keyJoined[9-1];

#else

	key[k-1][0] = keyJoined[14-1];

	key[k-1][1] = keyJoined[17-1];

	key[k-1][2] = keyJoined[11-1];

	key[k-1][3] = keyJoined[24-1];

	key[k-1][4] = keyJoined[1-1];

	key[k-1][5] = keyJoined[5-1];

	key[k-1][6] = keyJoined[3-1];

	key[k-1][7] = keyJoined[28-1];

	key[k-1][8] = keyJoined[15-1];

	key[k-1][9] = keyJoined[6-1];

	key[k-1][10] = keyJoined[21-1];

	key[k-1][11] = keyJoined[10-1];

	key[k-1][12] = keyJoined[23-1];

	key[k-1][13] = keyJoined[19-1];

	key[k-1][14] = keyJoined[12-1];

	key[k-1][15] = keyJoined[4-1];

	key[k-1][16] = keyJoined[26-1];

	key[k-1][17] = keyJoined[8-1];

	key[k-1][18] = keyJoined[16-1];

	key[k-1][19] = keyJoined[7-1];

	key[k-1][20] = keyJoined[27-1];

	key[k-1][21] = keyJoined[20-1];

	key[k-1][22] = keyJoined[13-1];

	key[k-1][23] = keyJoined[2-1];

	key[k-1][24] = keyJoined[41-1];

	key[k-1][25] = keyJoined[52-1];

	key[k-1][26] = keyJoined[31-1];

	key[k-1][27] = keyJoined[37-1];

	key[k-1][28] = keyJoined[47-1];

	key[k-1][29] = keyJoined[55-1];

	key[k-1][30] = keyJoined[30-1];

	key[k-1][31] = keyJoined[40-1];

	key[k-1][32] = keyJoined[51-1];

	key[k-1][33] = keyJoined[45-1];

	key[k-1][34] = keyJoined[33-1];

	key[k-1][35] = keyJoined[48-1];

	key[k-1][36] = keyJoined[44-1];

	key[k-1][37] = keyJoined[49-1];

	key[k-1][38] = keyJoined[39-1];

	key[k-1][39] = keyJoined[56-1];

	key[k-1][40] = keyJoined[34-1];

	key[k-1][41] = keyJoined[53-1];

	key[k-1][42] = keyJoined[46-1];

	key[k-1][43] = keyJoined[42-1];

	key[k-1][44] = keyJoined[50-1];

	key[k-1][45] = keyJoined[36-1];

	key[k-1][46] = keyJoined[29-1];

	key[k-1][47] = keyJoined[32-1];

#endif

}



char* CDES::DataIP()

{

	char *dataIP = new char[DATA_LENGTH];



	dataIP[0] = data[2-1];

	dataIP[1] = data[6-1];

	dataIP[2] = data[3-1];

	dataIP[3] = data[1-1];

	dataIP[4] = data[4-1];

	dataIP[5] = data[8-1];

	dataIP[6] = data[5-1];

	dataIP[7] = data[7-1];



	return dataIP;

}



char* CDES::DataIP_DES()

{

	char *dataIP = new char[DATA_LENGTH];



	dataIP[0] = data[58-1];

	dataIP[1] = data[50-1];

	dataIP[2] = data[42-1];

	dataIP[3] = data[34-1];

	dataIP[4] = data[26-1];

	dataIP[5] = data[18-1];

	dataIP[6] = data[10-1];

	dataIP[7] = data[2-1];

	dataIP[8] = data[60-1];

	dataIP[9] = data[52-1];

	dataIP[10] = data[44-1];

	dataIP[11] = data[36-1];

	dataIP[12] = data[28-1];

	dataIP[13] = data[20-1];

	dataIP[14] = data[12-1];

	dataIP[15] = data[4-1];

	dataIP[16] = data[62-1];

	dataIP[17] = data[54-1];

	dataIP[18] = data[46-1];

	dataIP[19] = data[38-1];

	dataIP[20] = data[30-1];

	dataIP[21] = data[22-1];

	dataIP[22] = data[14-1];

	dataIP[23] = data[6-1];

	dataIP[24] = data[64-1];

	dataIP[25] = data[56-1];

	dataIP[26] = data[48-1];

	dataIP[27] = data[40-1];

	dataIP[28] = data[32-1];

	dataIP[29] = data[24-1];

	dataIP[30] = data[16-1];

	dataIP[31] = data[8-1];

	dataIP[32] = data[57-1];

	dataIP[33] = data[49-1];

	dataIP[34] = data[41-1];

	dataIP[35] = data[33-1];

	dataIP[36] = data[25-1];

	dataIP[37] = data[17-1];

	dataIP[38] = data[9-1];

	dataIP[39] = data[1-1];

	dataIP[40] = data[59-1];

	dataIP[41] = data[51-1];

	dataIP[42] = data[43-1];

	dataIP[43] = data[35-1];

	dataIP[44] = data[27-1];

	dataIP[45] = data[19-1];

	dataIP[46] = data[11-1];

	dataIP[47] = data[3-1];

	dataIP[48] = data[61-1];

	dataIP[49] = data[53-1];

	dataIP[50] = data[45-1];

	dataIP[51] = data[37-1];

	dataIP[52] = data[29-1];

	dataIP[53] = data[21-1];

	dataIP[54] = data[13-1];

	dataIP[55] = data[5-1];

	dataIP[56] = data[63-1];

	dataIP[57] = data[55-1];

	dataIP[58] = data[47-1];

	dataIP[59] = data[39-1];

	dataIP[60] = data[31-1];

	dataIP[61] = data[23-1];

	dataIP[62] = data[15-1];

	dataIP[63] = data[7-1];



	return dataIP;

}



char* CDES::ExtendedPermutation(char *right)

{

	char* ep = new char[KEY_P_LENGTH];

	int i = DATA_LENGTH/2;



#ifdef SDES

	ep[0] = right[i+4-1];

	ep[1] = right[i+1-1];

	ep[2] = right[i+2-1];

	ep[3] = right[i+3-1];

	ep[4] = right[i+2-1];

	ep[5] = right[i+3-1];

	ep[6] = right[i+4-1];

	ep[7] = right[i+1-1];

#else



	ep[0] = right[i+32-1];

	ep[1] = right[i+1-1];

	ep[2] = right[i+2-1];

	ep[3] = right[i+3-1];

	ep[4] = right[i+4-1];

	ep[5] = right[i+5-1];

	ep[6] = right[i+4-1];

	ep[7] = right[i+5-1];

	ep[8] = right[i+6-1];

	ep[9] = right[i+7-1];

	ep[10] = right[i+8-1];

	ep[11] = right[i+9-1];

	ep[12] = right[i+8-1];

	ep[13] = right[i+9-1];

	ep[14] = right[i+10-1];

	ep[15] = right[i+11-1];

	ep[16] = right[i+12-1];

	ep[17] = right[i+13-1];

	ep[18] = right[i+12-1];

	ep[19] = right[i+13-1];

	ep[20] = right[i+14-1];

	ep[21] = right[i+15-1];

	ep[22] = right[i+16-1];

	ep[23] = right[i+17-1];

	ep[24] = right[i+16-1];

	ep[25] = right[i+17-1];

	ep[26] = right[i+18-1];

	ep[27] = right[i+19-1];

	ep[28] = right[i+20-1];

	ep[29] = right[i+21-1];

	ep[30] = right[i+20-1];

	ep[31] = right[i+21-1];

	ep[32] = right[i+22-1];

	ep[33] = right[i+23-1];

	ep[34] = right[i+24-1];

	ep[35] = right[i+25-1];

	ep[36] = right[i+24-1];

	ep[37] = right[i+25-1];

	ep[38] = right[i+26-1];

	ep[39] = right[i+27-1];

	ep[40] = right[i+28-1];

	ep[41] = right[i+29-1];

	ep[42] = right[i+28-1];

	ep[43] = right[i+29-1];

	ep[44] = right[i+30-1];

	ep[45] = right[i+31-1];

	ep[46] = right[i+32-1];

	ep[47] = right[i+1-1];



#endif



	return ep;

}



char* CDES::XORwithKey(char *b, int k)

{

	char *result = new char[DATA_LENGTH];

	int i;



	for (i = 0 ; i < DATA_LENGTH ; i++)

	{

		result[i] = XOR(b[i],key[k-1][i]);

	}



	return result;

}



char CDES::XOR(char a, char b)

{

	if (a == b)

		return '0';

	else

		return '1';

}



void CDES::FillS0_SDES()

{

	S[0][0][0] = 1;

	S[0][0][1] = 0;

	S[0][0][2] = 3;

	S[0][0][3] = 2;



	S[0][1][0] = 3;

	S[0][1][1] = 2;

	S[0][1][2] = 1;

	S[0][1][3] = 0;



	S[0][2][0] = 0;

	S[0][2][1] = 2;

	S[0][2][2] = 1;

	S[0][2][3] = 3;



	S[0][3][0] = 3;

	S[0][3][1] = 1;

	S[0][3][2] = 3;

	S[0][3][3] = 2;

}



void CDES::FillS1_SDES()

{

	S[1][0][0] = 0;

	S[1][0][1] = 1;

	S[1][0][2] = 2;

	S[1][0][3] = 3;



	S[1][1][0] = 2;

	S[1][1][1] = 0;

	S[1][1][2] = 1;

	S[1][1][3] = 3;



	S[1][2][0] = 3;

	S[1][2][1] = 0;

	S[1][2][2] = 1;

	S[1][2][3] = 0;



	S[1][3][0] = 2;

	S[1][3][1] = 1;

	S[1][3][2] = 0;

	S[1][3][3] = 3;

}



char* CDES::GetSValue(char *b, int s)

{

	char ra,rb,ca,cb;

	char* svalue;



#ifdef SDES

	if (s == 0)			// value from S0

	{

		ra = b[1-1];

		rb = b[4-1];



		ca = b[2-1];

		cb = b[3-1];

	}

	else if (s == 1)	// value from S1

	{

		ra = b[5-1];

		rb = b[8-1];



		ca = b[6-1];

		cb = b[7-1];

	}

	

	svalue = Bin2bit(GetValue(Dec2bit(ra,rb),Dec2bit(ca,cb),s));

#else

	char cc,cd;



	if (s == 0)

	{

		ra = b[1-1];

		rb = b[6-1];



		ca = b[2-1];

		cb = b[3-1];

		cc = b[4-1];

		cd = b[5-1];

	}

	else if (s == 1)

	{

		ra = b[7-1];

		rb = b[12-1];



		ca = b[8-1];

		cb = b[9-1];

		cc = b[10-1];

		cd = b[11-1];

	}

	else if (s == 2)

	{

		ra = b[13-1];

		rb = b[18-1];



		ca = b[14-1];

		cb = b[15-1];

		cc = b[16-1];

		cd = b[17-1];

	}

	else if (s == 3)

	{

		ra = b[19-1];

		rb = b[24-1];



		ca = b[20-1];

		cb = b[21-1];

		cc = b[22-1];

		cd = b[23-1];

	}

	else if (s == 4)

	{

		ra = b[25-1];

		rb = b[30-1];



		ca = b[26-1];

		cb = b[27-1];

		cc = b[28-1];

		cd = b[29-1];

	}

	else if (s == 5)

	{

		ra = b[31-1];

		rb = b[36-1];



		ca = b[32-1];

		cb = b[33-1];

		cc = b[34-1];

		cd = b[35-1];

	}

	else if (s == 6)

	{

		ra = b[37-1];

		rb = b[42-1];



		ca = b[38-1];

		cb = b[39-1];

		cc = b[40-1];

		cd = b[41-1];

	}

	else if (s == 7)

	{

		ra = b[43-1];

		rb = b[48-1];



		ca = b[44-1];

		cb = b[45-1];

		cc = b[46-1];

		cd = b[47-1];

	}



	svalue = Bin4bit(GetValue(Dec2bit(ra,rb),Dec4bit(ca,cb,cc,cd),s));

#endif

	return svalue;

}



int CDES::GetValue(int a, int b, int s)

{

	cout << endl << "Getting S" << s << " value of " << a << " " << b;



	return S[s][a][b];

}



int CDES::Dec2bit(char a, char b)

{

	if (a == '0' && b == '0')

		return 0;

	else if (a == '0' && b == '1')

		return 1;

	else if (a == '1' && b == '0')

		return 2;

	else

		return 3;

}



int CDES::Dec4bit(char a, char b, char c, char d)

{

	if		(a == '0' && b == '0' && c == '0' && d == '0')

		return 0;

	else if (a == '0' && b == '0' && c == '0' && d == '1')

		return 1;

	else if (a == '0' && b == '0' && c == '1' && d == '0')

		return 2;

	else if (a == '0' && b == '0' && c == '1' && d == '1')

		return 3;

	else if (a == '0' && b == '1' && c == '0' && d == '0')

		return 4;

	else if (a == '0' && b == '1' && c == '0' && d == '1')

		return 5;

	else if (a == '0' && b == '1' && c == '1' && d == '0')

		return 6;

	else if (a == '0' && b == '1' && c == '1' && d == '1')

		return 7;

	else if (a == '1' && b == '0' && c == '0' && d == '0')

		return 8;

	else if (a == '1' && b == '0' && c == '0' && d == '1')

		return 9;

	else if (a == '1' && b == '0' && c == '1' && d == '0')

		return 10;

	else if (a == '1' && b == '0' && c == '1' && d == '1')

		return 11;

	else if (a == '1' && b == '1' && c == '0' && d == '0')

		return 12;

	else if (a == '1' && b == '1' && c == '0' && d == '1')

		return 13;

	else if (a == '1' && b == '1' && c == '1' && d == '0')

		return 14;

	else

		return 15;

}



char* CDES::Bin2bit(int a)

{

	if (a == 0)

		return "00";

	else if (a == 1)

		return "01";

	else if (a == 2)

		return "10";

	else

		return "11";

}



char* CDES::Bin4bit(int a)

{

	if		(a == 0)

		return "0000";

	else if (a == 1)

		return "0001";

	else if (a == 2)

		return "0010";

	else if (a == 3)

		return "0011";

	else if (a == 4)

		return "0100";

	else if (a == 5)

		return "0101";

	else if (a == 6)

		return "0110";

	else if (a == 7)

		return "0111";

	else if (a == 8)

		return "1000";

	else if (a == 9)

		return "1001";

	else if (a == 10)

		return "1010";

	else if (a == 11)

		return "1011";

	else if (a == 12)

		return "1100";

	else if (a == 13)

		return "1101";

	else if (a == 14)

		return "1110";

	else

		return "1111";

}



char* CDES::JoinSres(char *r1, char *r2)

{

	char *res = new char[DATA_LENGTH/2];

	int i,j;



	for (i = 0 ; i < ((DATA_LENGTH/2)/2) ; i++)

	{

		res[i] = r1[i];

	}



	for (i = ((DATA_LENGTH/2)/2),j = 0 ; j < ((DATA_LENGTH/2)/2) ; i++,j++)

	{

		res[i] = r2[j];

	}



	return res;

}



char* CDES::PermuteSres(char *sr)

{

	char *r = new char[(DATA_LENGTH/2)];



	r[0] = sr[2-1];

	r[1] = sr[4-1];

	r[2] = sr[3-1];

	r[3] = sr[1-1];



	return r;

}



void CDES::SampleKeys()

{

	key[1-1][0] = '1';

	key[1-1][1] = '0';

	key[1-1][2] = '1';

	key[1-1][3] = '0';

	key[1-1][4] = '0';

	key[1-1][5] = '1';

	key[1-1][6] = '0';

	key[1-1][7] = '0';



	key[2-1][0] = '0';

	key[2-1][1] = '1';

	key[2-1][2] = '0';

	key[2-1][3] = '0';

	key[2-1][4] = '0';

	key[2-1][5] = '0';

	key[2-1][6] = '1';

	key[2-1][7] = '1';

}



void CDES::print(char *d, int length)

{

	int i;



	cout << endl;

	for (i = 0 ; i < length ; i++)

	{

		cout << d[i];

	}

	cout << endl;

}



char* CDES::XORLandP(char *left, char *p4r)

{

	int i;

	char *res = new char[DATA_LENGTH/2];



	for (i = 0 ; i < (DATA_LENGTH/2) ; i++)

	{

		res[i] = XOR(left[i],p4r[i]);

	}



	return res;

}



char* CDES::FKFinal(char *xr, char *right)

{

	char* res = new char[DATA_LENGTH];

	int i;



	for (i = 0 ; i < (DATA_LENGTH/2) ; i++)

	{

		res[i] = xr[i];

	}



	for (i = (DATA_LENGTH/2) ; i < DATA_LENGTH ; i++)

	{

		res[i] = right[i];

	}



	return res;

}



char* CDES::FKFunction(char *ip,int f)

{

	// begin the KF function

	char *ep = ExtendedPermutation(ip);



	cout << endl << "Extended Permutation";

	print(ep,KEY_P_LENGTH);



	cout << endl << "The k" << f;

	print(key[f-1],KEY_P_LENGTH);



	char *keyXor = XORwithKey(ep,f);



	cout << endl << "XOR with k" << f;

	print(keyXor,KEY_P_LENGTH);



	char *S0res = GetSValue(keyXor,0);



	cout << endl << "S0 Result";

#ifdef SDES

	print(S0res,DATA_LENGTH/4);

#else

	print(S0res,4);

#endif



	char *S1res = GetSValue(keyXor,1);



	cout << endl << "S1 Result";

#ifdef SDES

	print(S1res,DATA_LENGTH/4);

#else

	print(S1res,4);

#endif



#ifdef DES

	char *S2res = GetSValue(keyXor,2);

	cout << endl << "S2 Result";

	print(S2res,4);



	char *S3res = GetSValue(keyXor,3);

	cout << endl << "S3 Result";

	print(S3res,4);



	char *S4res = GetSValue(keyXor,4);

	cout << endl << "S4 Result";

	print(S4res,4);



	char *S5res = GetSValue(keyXor,5);

	cout << endl << "S5 Result";

	print(S5res,4);



	char *S6res = GetSValue(keyXor,6);

	cout << endl << "S6 Result";

	print(S6res,4);



	char *S7res = GetSValue(keyXor,7);

	cout << endl << "S7 Result";

	print(S7res,4);

#endif



#ifdef SDES

	char *Sresult = JoinSres(S0res,S1res);

	cout << endl << "Joined S0 and S1 Results";

#else

	char *Sresult = JoinSres_DES(S0res,S1res,S2res,S3res,S4res,S5res,S6res,S7res);

	cout << endl << "Joined Printed S Results";

#endif



	print(Sresult,DATA_LENGTH/2);



#ifdef SDES

	char *pSres = PermuteSres(Sresult);

	cout << endl << "Permutation P4";

#else

	char *pSres = PermuteSres_DES(Sresult);

	cout << endl << "Permutation P32";

#endif



	print(pSres,DATA_LENGTH/2);



	char *XorLandPr = XORLandP(ip,pSres);

#ifdef SDES

	cout << endl << "XOR L and P4 Result";

#else

	cout << endl << "XOR L and P32 Result";

#endif



	print(XorLandPr,DATA_LENGTH/2);



	char *FKFinalRes = FKFinal(XorLandPr,ip);



	return FKFinalRes;

}



char* CDES::Switch(char *p)

{

	int i,j;

	char *res = new char[DATA_LENGTH];



	for (i = 0,j = (DATA_LENGTH/2) ; i < (DATA_LENGTH/2) ; i++,j++)

	{

		res[i] = p[j];

	}



	for (i = (DATA_LENGTH/2),j = 0 ; i < DATA_LENGTH ; i++,j++)

	{

		res[i] = p[j];

	}



	return res;

}



char* CDES::IPInverse(char *r)

{

	char *res = new char[DATA_LENGTH];



#ifdef SDES

	res[0] = r[4-1];

	res[1] = r[1-1];

	res[2] = r[3-1];

	res[3] = r[5-1];

	res[4] = r[7-1];

	res[5] = r[2-1];

	res[6] = r[8-1];

	res[7] = r[6-1];

#else

	res[0] = r[40-1];

	res[1] = r[8-1];

	res[2] = r[48-1];

	res[3] = r[16-1];

	res[4] = r[56-1];

	res[5] = r[24-1];

	res[6] = r[64-1];

	res[7] = r[32-1];

	res[8] = r[39-1];

	res[9] = r[7-1];

	res[10] = r[47-1];

	res[11] = r[15-1];

	res[12] = r[55-1];

	res[13] = r[23-1];

	res[14] = r[63-1];

	res[15] = r[31-1];

	res[16] = r[38-1];

	res[17] = r[6-1];

	res[18] = r[46-1];

	res[19] = r[14-1];

	res[20] = r[54-1];

	res[21] = r[22-1];

	res[22] = r[62-1];

	res[23] = r[30-1];

	res[24] = r[37-1];

	res[25] = r[5-1];

	res[26] = r[45-1];

	res[27] = r[13-1];

	res[28] = r[53-1];

	res[29] = r[21-1];

	res[30] = r[61-1];

	res[31] = r[29-1];

	res[32] = r[36-1];

	res[33] = r[4-1];

	res[34] = r[44-1];

	res[35] = r[12-1];

	res[36] = r[52-1];

	res[37] = r[20-1];

	res[38] = r[60-1];

	res[39] = r[28-1];

	res[40] = r[35-1];

	res[41] = r[3-1];

	res[42] = r[43-1];

	res[43] = r[11-1];

	res[44] = r[51-1];

	res[45] = r[19-1];

	res[46] = r[59-1];

	res[47] = r[27-1];

	res[48] = r[34-1];

	res[49] = r[2-1];

	res[50] = r[42-1];

	res[51] = r[10-1];

	res[52] = r[50-1];

	res[53] = r[18-1];

	res[54] = r[58-1];

	res[55] = r[26-1];

	res[56] = r[33-1];

	res[57] = r[1-1];

	res[58] = r[41-1];

	res[59] = r[9-1];

	res[60] = r[49-1];

	res[61] = r[17-1];

	res[62] = r[57-1];

	res[63] = r[25-1];

#endif



	return res;

}



char* CDES::Decrypt()

{

	// Calculate Keys

	GenKeys();



	// Begin Encryption

#ifdef SDES

	char *ip = DataIP(); // Initial Permutation on Input bits

#else

	char *ip = DataIP_DES();

#endif



	cout << endl << "Initial Permutation";

	print(ip,DATA_LENGTH);



	char *loopData = ip;

	char *FKr;



	for (int i = NO_OF_KEYS ; i >= 1 ; i--)

	{

		FKr = FKFunction(loopData,i);



		cout << endl << "FK" << i << " Result";

		print(FKr,DATA_LENGTH);



		if (i != 1)

		{

			loopData = Switch(FKr);

			

			cout << endl << "Switch Result";

			print(loopData,DATA_LENGTH);

		}

		else

		{

			loopData = FKr;

		}

	}



	char *IPinv = IPInverse(loopData);



	cout << endl << "IP Inverse";

	print(IPinv,DATA_LENGTH);



	return IPinv;

}



void CDES::FillAllS()

{

#ifdef SDES

	FillS0_SDES();

	FillS1_SDES();

#else DES

	FillS0_DES();

	FillS1_DES();

	FillS2_DES();

	FillS3_DES();

	FillS4_DES();

	FillS5_DES();

	FillS6_DES();

	FillS7_DES();

#endif

}



void CDES::FillS0_DES()

{

	S[0][0][0] = 14;	S[0][0][1] = 4;		S[0][0][2] = 13;	S[0][0][3] = 1;

	S[0][0][4] = 2;		S[0][0][5] = 15;	S[0][0][6] = 11;	S[0][0][7] = 8;

	S[0][0][8] = 3;		S[0][0][9] = 10;	S[0][0][10] = 6;	S[0][0][11] = 12;

	S[0][0][12] = 5;	S[0][0][13] = 9;	S[0][0][14] = 0;	S[0][0][15] = 7;



	S[0][1][0] = 0;		S[0][1][1] = 15;	S[0][1][2] = 7;		S[0][1][3] = 4;

	S[0][1][4] = 14;	S[0][1][5] = 2;		S[0][1][6] = 13;	S[0][1][7] = 1;

	S[0][1][8] = 10;	S[0][1][9] = 6;		S[0][1][10] = 12;	S[0][1][11] = 11;

	S[0][1][12] = 9;	S[0][1][13] = 5;	S[0][1][14] = 3;	S[0][1][15] = 8;



	S[0][2][0] = 4;		S[0][2][1] = 1;		S[0][2][2] = 14;	S[0][2][3] = 8;

	S[0][2][4] = 13;	S[0][2][5] = 6;		S[0][2][6] = 2;		S[0][2][7] = 11;

	S[0][2][8] = 15;	S[0][2][9] = 12;	S[0][2][10] = 9;	S[0][2][11] = 7;

	S[0][2][12] = 3;	S[0][2][13] = 10;	S[0][2][14] = 5;	S[0][2][15] = 0;



	S[0][3][0] = 15;	S[0][3][1] = 12;	S[0][3][2] = 8;		S[0][3][3] = 2;

	S[0][3][4] = 4;		S[0][3][5] = 9;		S[0][3][6] = 1;		S[0][3][7] = 7;

	S[0][3][8] = 5;		S[0][3][9] = 11;	S[0][3][10] = 3;	S[0][3][11] = 14;

	S[0][3][12] = 10;	S[0][3][13] = 0;	S[0][3][14] = 6;	S[0][3][15] = 13;

}



void CDES::FillS1_DES()

{

	S[1][0][0] = 15;	S[1][0][1] = 1;		S[1][0][2] = 8;		S[1][0][3] = 14;

	S[1][0][4] = 6;		S[1][0][5] = 11;	S[1][0][6] = 3;		S[1][0][7] = 4;

	S[1][0][8] = 9;		S[1][0][9] = 7;		S[1][0][10] = 2;	S[1][0][11] = 13;

	S[1][0][12] = 12;	S[1][0][13] = 0;	S[1][0][14] = 5;	S[1][0][15] = 10;



	S[1][1][0] = 3;		S[1][1][1] = 13;	S[1][1][2] = 4;		S[1][1][3] = 7;

	S[1][1][4] = 15;	S[1][1][5] = 2;		S[1][1][6] = 8;		S[1][1][7] = 14;

	S[1][1][8] = 12;	S[1][1][9] = 0;		S[1][1][10] = 1;	S[1][1][11] = 10;

	S[1][1][12] = 6;	S[1][1][13] = 9;	S[1][1][14] = 11;	S[1][1][15] = 5;



	S[1][2][0] = 0;		S[1][2][1] = 14;	S[1][2][2] = 7;		S[1][2][3] = 11;

	S[1][2][4] = 10;	S[1][2][5] = 4;		S[1][2][6] = 13;	S[1][2][7] = 1;

	S[1][2][8] = 5;		S[1][2][9] = 8;		S[1][2][10] = 12;	S[1][2][11] = 6;

	S[1][2][12] = 9;	S[1][2][13] = 3;	S[1][2][14] = 2;	S[1][2][15] = 15;



	S[1][3][0] = 13;	S[1][3][1] = 8;		S[1][3][2] = 10;	S[1][3][3] = 1;

	S[1][3][4] = 3;		S[1][3][5] = 15;	S[1][3][6] = 4;		S[1][3][7] = 2;

	S[1][3][8] = 11;	S[1][3][9] = 6;		S[1][3][10] = 7;	S[1][3][11] = 12;

	S[1][3][12] = 0;	S[1][3][13] = 5;	S[1][3][14] = 14;	S[1][3][15] = 9;

}



void CDES::FillS2_DES()

{

	S[2][0][0] = 10;	S[2][0][1] = 0;		S[2][0][2] = 9;		S[2][0][3] = 14;

	S[2][0][4] = 6;		S[2][0][5] = 3;		S[2][0][6] = 15;	S[2][0][7] = 5;

	S[2][0][8] = 1;		S[2][0][9] = 13;	S[2][0][10] = 12;	S[2][0][11] = 7;

	S[2][0][12] = 11;	S[2][0][13] = 4;	S[2][0][14] = 2;	S[2][0][15] = 8;



	S[2][1][0] = 13;	S[2][1][1] = 7;		S[2][1][2] = 0;		S[2][1][3] = 9;

	S[2][1][4] = 3;		S[2][1][5] = 4;		S[2][1][6] = 6;		S[2][1][7] = 10;

	S[2][1][8] = 2;		S[2][1][9] = 8;		S[2][1][10] = 5;	S[2][1][11] = 14;

	S[2][1][12] = 12;	S[2][1][13] = 11;	S[2][1][14] = 15;	S[2][1][15] = 1;



	S[2][2][0] = 13;	S[2][2][1] = 6;		S[2][2][2] = 4;		S[2][2][3] = 9;

	S[2][2][4] = 8;		S[2][2][5] = 15;	S[2][2][6] = 3;		S[2][2][7] = 0;

	S[2][2][8] = 11;	S[2][2][9] = 1;		S[2][2][10] = 2;	S[2][2][11] = 12;

	S[2][2][12] = 5;	S[2][2][13] = 10;	S[2][2][14] = 14;	S[2][2][15] = 7;



	S[2][3][0] = 1;		S[2][3][1] = 10;	S[2][3][2] = 13;	S[2][3][3] = 0;

	S[2][3][4] = 6;		S[2][3][5] = 9;		S[2][3][6] = 8;		S[2][3][7] = 7;

	S[2][3][8] = 4;		S[2][3][9] = 15;	S[2][3][10] = 14;	S[2][3][11] = 3;

	S[2][3][12] = 11;	S[2][3][13] = 5;	S[2][3][14] = 2;	S[2][3][15] = 12;

}



void CDES::FillS3_DES()

{

	S[3][0][0] = 7;		S[3][0][1] = 13;	S[3][0][2] = 14;	S[3][0][3] = 3;

	S[3][0][4] = 0;		S[3][0][5] = 6;		S[3][0][6] = 9;		S[3][0][7] = 10;

	S[3][0][8] = 1;		S[3][0][9] = 2;		S[3][0][10] = 8;	S[3][0][11] = 5;

	S[3][0][12] = 11;	S[3][0][13] = 12;	S[3][0][14] = 4;	S[3][0][15] = 15;



	S[3][1][0] = 13;	S[3][1][1] = 8;		S[3][1][2] = 11;	S[3][1][3] = 5;

	S[3][1][4] = 6;		S[3][1][5] = 15;	S[3][1][6] = 0;		S[3][1][7] = 3;

	S[3][1][8] = 4;		S[3][1][9] = 7;		S[3][1][10] = 2;	S[3][1][11] = 12;

	S[3][1][12] = 1;	S[3][1][13] = 10;	S[3][1][14] = 14;	S[3][1][15] = 9;



	S[3][2][0] = 10;	S[3][2][1] = 6;		S[3][2][2] = 9;		S[3][2][3] = 0;

	S[3][2][4] = 12;	S[3][2][5] = 11;	S[3][2][6] = 7;		S[3][2][7] = 13;

	S[3][2][8] = 15;	S[3][2][9] = 1;		S[3][2][10] = 3;	S[3][2][11] = 14;

	S[3][2][12] = 5;	S[3][2][13] = 2;	S[3][2][14] = 8;	S[3][2][15] = 4;



	S[3][3][0] = 3;		S[3][3][1] = 15;	S[3][3][2] = 0;		S[3][3][3] = 6;

	S[3][3][4] = 10;	S[3][3][5] = 1;		S[3][3][6] = 13;	S[3][3][7] = 8;

	S[3][3][8] = 9;		S[3][3][9] = 4;		S[3][3][10] = 5;	S[3][3][11] = 11;

	S[3][3][12] = 12;	S[3][3][13] = 7;	S[3][3][14] = 2;	S[3][3][15] = 14;

}



void CDES::FillS4_DES()

{

	S[4][0][0] = 2;		S[4][0][1] = 12;	S[4][0][2] = 4;		S[4][0][3] = 1;

	S[4][0][4] = 7;		S[4][0][5] = 10;	S[4][0][6] = 11;	S[4][0][7] = 6;

	S[4][0][8] = 8;		S[4][0][9] = 5;		S[4][0][10] = 3;	S[4][0][11] = 15;

	S[4][0][12] = 13;	S[4][0][13] = 0;	S[4][0][14] = 14;	S[4][0][15] = 9;



	S[4][1][0] = 14;	S[4][1][1] = 11;	S[4][1][2] = 2;		S[4][1][3] = 12;

	S[4][1][4] = 4;		S[4][1][5] = 7;		S[4][1][6] = 13;	S[4][1][7] = 1;

	S[4][1][8] = 5;		S[4][1][9] = 0;		S[4][1][10] = 15;	S[4][1][11] = 10;

	S[4][1][12] = 3;	S[4][1][13] = 9;	S[4][1][14] = 8;	S[4][1][15] = 6;



	S[4][2][0] = 4;		S[4][2][1] = 2;		S[4][2][2] = 1;		S[4][2][3] = 11;

	S[4][2][4] = 10;	S[4][2][5] = 13;	S[4][2][6] = 7;		S[4][2][7] = 8;

	S[4][2][8] = 15;	S[4][2][9] = 9;		S[4][2][10] = 12;	S[4][2][11] = 5;

	S[4][2][12] = 6;	S[4][2][13] = 3;	S[4][2][14] = 0;	S[4][2][15] = 14;



	S[4][3][0] = 11;	S[4][3][1] = 8;		S[4][3][2] = 12;	S[4][3][3] = 7;

	S[4][3][4] = 1;		S[4][3][5] = 14;	S[4][3][6] = 2;		S[4][3][7] = 13;

	S[4][3][8] = 6;		S[4][3][9] = 15;	S[4][3][10] = 0;	S[4][3][11] = 9;

	S[4][3][12] = 10;	S[4][3][13] = 4;	S[4][3][14] = 5;	S[4][3][15] = 3;

}



void CDES::FillS5_DES()

{

	S[5][0][0] = 12;	S[5][0][1] = 1;		S[5][0][2] = 10;	S[5][0][3] = 15;

	S[5][0][4] = 9;		S[5][0][5] = 2;		S[5][0][6] = 6;		S[5][0][7] = 8;

	S[5][0][8] = 0;		S[5][0][9] = 13;	S[5][0][10] = 3;	S[5][0][11] = 4;

	S[5][0][12] = 14;	S[5][0][13] = 7;	S[5][0][14] = 5;	S[5][0][15] = 11;



	S[5][1][0] = 10;	S[5][1][1] = 15;	S[5][1][2] = 4;		S[5][1][3] = 2;

	S[5][1][4] = 7;		S[5][1][5] = 12;	S[5][1][6] = 9;		S[5][1][7] = 5;

	S[5][1][8] = 6;		S[5][1][9] = 1;		S[5][1][10] = 13;	S[5][1][11] = 14;

	S[5][1][12] = 0;	S[5][1][13] = 11;	S[5][1][14] = 3;	S[5][1][15] = 8;



	S[5][2][0] = 9;		S[5][2][1] = 14;	S[5][2][2] = 15;	S[5][2][3] = 5;

	S[5][2][4] = 2;		S[5][2][5] = 8;		S[5][2][6] = 12;	S[5][2][7] = 3;

	S[5][2][8] = 7;		S[5][2][9] = 0;		S[5][2][10] = 4;	S[5][2][11] = 10;

	S[5][2][12] = 1;	S[5][2][13] = 13;	S[5][2][14] = 11;	S[5][2][15] = 6;



	S[5][3][0] = 4;		S[5][3][1] = 3;		S[5][3][2] = 2;		S[5][3][3] = 12;

	S[5][3][4] = 9;		S[5][3][5] = 5;		S[5][3][6] = 15;	S[5][3][7] = 10;

	S[5][3][8] = 11;	S[5][3][9] = 14;	S[5][3][10] = 1;	S[5][3][11] = 7;

	S[5][3][12] = 6;	S[5][3][13] = 0;	S[5][3][14] = 8;	S[5][3][15] = 13;

}



void CDES::FillS6_DES()

{

	S[6][0][0] = 4;		S[6][0][1] = 11;	S[6][0][2] = 2;		S[6][0][3] = 14;

	S[6][0][4] = 15;	S[6][0][5] = 0;		S[6][0][6] = 8;		S[6][0][7] = 13;

	S[6][0][8] = 3;		S[6][0][9] = 12;	S[6][0][10] = 9;	S[6][0][11] = 7;

	S[6][0][12] = 5;	S[6][0][13] = 10;	S[6][0][14] = 6;	S[6][0][15] = 1;



	S[6][1][0] = 13;	S[6][1][1] = 0;		S[6][1][2] = 11;	S[6][1][3] = 7;

	S[6][1][4] = 4;		S[6][1][5] = 9;		S[6][1][6] = 1;		S[6][1][7] = 10;

	S[6][1][8] = 14;	S[6][1][9] = 3;		S[6][1][10] = 5;	S[6][1][11] = 12;

	S[6][1][12] = 2;	S[6][1][13] = 15;	S[6][1][14] = 8;	S[6][1][15] = 6;



	S[6][2][0] = 1;		S[6][2][1] = 4;		S[6][2][2] = 11;	S[6][2][3] = 13;

	S[6][2][4] = 12;	S[6][2][5] = 3;		S[6][2][6] = 7;		S[6][2][7] = 14;

	S[6][2][8] = 10;	S[6][2][9] = 15;	S[6][2][10] = 6;	S[6][2][11] = 8;

	S[6][2][12] = 0;	S[6][2][13] = 5;	S[6][2][14] = 9;	S[6][2][15] = 2;



	S[6][3][0] = 6;		S[6][3][1] = 11;	S[6][3][2] = 13;	S[6][3][3] = 8;

	S[6][3][4] = 1;		S[6][3][5] = 4;		S[6][3][6] = 10;	S[6][3][7] = 7;

	S[6][3][8] = 9;		S[6][3][9] = 5;		S[6][3][10] = 0;	S[6][3][11] = 15;

	S[6][3][12] = 14;	S[6][3][13] = 2;	S[6][3][14] = 3;	S[6][3][15] = 12;

}



void CDES::FillS7_DES()

{

	S[7][0][0] = 13;	S[7][0][1] = 2;		S[7][0][2] = 8;		S[7][0][3] = 4;

	S[7][0][4] = 6;		S[7][0][5] = 15;	S[7][0][6] = 11;	S[7][0][7] = 1;

	S[7][0][8] = 10;	S[7][0][9] = 9;		S[7][0][10] = 3;	S[7][0][11] = 14;

	S[7][0][12] = 5;	S[7][0][13] = 0;	S[7][0][14] = 12;	S[7][0][15] = 7;



	S[7][1][0] = 1;		S[7][1][1] = 15;	S[7][1][2] = 13;	S[7][1][3] = 8;

	S[7][1][4] = 10;	S[7][1][5] = 3;		S[7][1][6] = 7;		S[7][1][7] = 4;

	S[7][1][8] = 12;	S[7][1][9] = 5;		S[7][1][10] = 6;	S[7][1][11] = 11;

	S[7][1][12] = 0;	S[7][1][13] = 14;	S[7][1][14] = 9;	S[7][1][15] = 2;



	S[7][2][0] = 7;		S[7][2][1] = 11;	S[7][2][2] = 4;		S[7][2][3] = 1;

	S[7][2][4] = 9;		S[7][2][5] = 12;	S[7][2][6] = 14;	S[7][2][7] = 2;

	S[7][2][8] = 0;		S[7][2][9] = 6;		S[7][2][10] = 10;	S[7][2][11] = 13;

	S[7][2][12] = 15;	S[7][2][13] = 3;	S[7][2][14] = 5;	S[7][2][15] = 8;



	S[7][3][0] = 2;		S[7][3][1] = 1;		S[7][3][2] = 14;	S[7][3][3] = 7;

	S[7][3][4] = 4;		S[7][3][5] = 10;	S[7][3][6] = 8;		S[7][3][7] = 13;

	S[7][3][8] = 15;	S[7][3][9] = 12;	S[7][3][10] = 9;	S[7][3][11] = 0;

	S[7][3][12] = 3;	S[7][3][13] = 5;	S[7][3][14] = 6;	S[7][3][15] = 11;

}



char* CDES::JoinSres_DES(char *a, char *b, char *c, char *d, char *e, char *f, char *g, char *h)

{

	char* JoinTres = new char[32];

	int i,j;



	for (i = 0 ; i < 4 ; i++)

	{

		JoinTres[i] = a[i];

	}



	for (i = 4,j = 0 ; i < 8 ; i++,j++)

	{

		JoinTres[i] = b[j];

	}



	for (i = 8,j = 0 ; i < 12 ; i++,j++)

	{

		JoinTres[i] = c[j];

	}



	for (i = 12,j = 0 ; i < 16 ; i++,j++)

	{

		JoinTres[i] = d[j];

	}



	for (i = 16,j = 0 ; i < 20 ; i++,j++)

	{

		JoinTres[i] = e[j];

	}



	for (i = 20,j = 0 ; i < 24 ; i++,j++)

	{

		JoinTres[i] = f[j];

	}



	for (i = 24,j = 0 ; i < 28 ; i++,j++)

	{

		JoinTres[i] = g[j];

	}



	for (i = 28,j = 0 ; i < 32 ; i++,j++)

	{

		JoinTres[i] = h[j];

	}



	return JoinTres;

}



char* CDES::PermuteSres_DES(char *r)

{

	char *res = new char[32];



	res[0] = r[16-1];

	res[1] = r[7-1];

	res[2] = r[20-1];

	res[3] = r[21-1];

	res[4] = r[29-1];

	res[5] = r[12-1];

	res[6] = r[28-1];

	res[7] = r[17-1];

	res[8] = r[1-1];

	res[9] = r[15-1];

	res[10] = r[23-1];

	res[11] = r[26-1];

	res[12] = r[5-1];

	res[13] = r[18-1];

	res[14] = r[31-1];

	res[15] = r[10-1];

	res[16] = r[2-1];

	res[17] = r[8-1];

	res[18] = r[24-1];

	res[19] = r[14-1];

	res[20] = r[32-1];

	res[21] = r[27-1];

	res[22] = r[3-1];

	res[23] = r[9-1];

	res[24] = r[19-1];

	res[25] = r[13-1];

	res[26] = r[30-1];

	res[27] = r[6-1];

	res[28] = r[22-1];

	res[29] = r[11-1];

	res[30] = r[4-1];

	res[31] = r[25-1];



	return res;

}



void CDES::GenKeys()

{

	char *keyPF = keyIPermutation();

	char *keyLshifted = LeftShift(keyPF,'L',1); // Left shift 1st Five bits to 1 bit

	char *keyRshifted = LeftShift(keyPF,'R',1); // Left shift 2nd Five bits to 1 bit

	

	keyPermutationA(JoinShifted(keyLshifted,keyRshifted),1); // create Key1



#ifdef SDES

	keyLshifted = LeftShift(keyPF,'L',3);

	keyRshifted = LeftShift(keyPF,'R',3);

	keyPermutationA(JoinShifted(keyLshifted,keyRshifted),2); // create Key2

#else

	keyLshifted = LeftShift(keyPF,'L',2);

	keyRshifted = LeftShift(keyPF,'R',2);

	keyPermutationA(JoinShifted(keyLshifted,keyRshifted),2); // create Key2



	keyLshifted = LeftShift(keyPF,'L',4);

	keyRshifted = LeftShift(keyPF,'R',4);

	keyPermutationA(JoinShifted(keyLshifted,keyRshifted),3); // create key3



	keyLshifted = LeftShift(keyPF,'L',6);

	keyRshifted = LeftShift(keyPF,'R',6);

	keyPermutationA(JoinShifted(keyLshifted,keyRshifted),4); // create key4



	keyLshifted = LeftShift(keyPF,'L',8);

	keyRshifted = LeftShift(keyPF,'R',8);

	keyPermutationA(JoinShifted(keyLshifted,keyRshifted),5); // create key5



	keyLshifted = LeftShift(keyPF,'L',10);

	keyRshifted = LeftShift(keyPF,'R',10);

	keyPermutationA(JoinShifted(keyLshifted,keyRshifted),6); // create key6



	keyLshifted = LeftShift(keyPF,'L',12);

	keyRshifted = LeftShift(keyPF,'R',12);

	keyPermutationA(JoinShifted(keyLshifted,keyRshifted),7); // create key7



	keyLshifted = LeftShift(keyPF,'L',14);

	keyRshifted = LeftShift(keyPF,'R',14);

	keyPermutationA(JoinShifted(keyLshifted,keyRshifted),8); // create key8



	keyLshifted = LeftShift(keyPF,'L',15);

	keyRshifted = LeftShift(keyPF,'R',15);

	keyPermutationA(JoinShifted(keyLshifted,keyRshifted),9); // create key9



	keyLshifted = LeftShift(keyPF,'L',17);

	keyRshifted = LeftShift(keyPF,'R',17);

	keyPermutationA(JoinShifted(keyLshifted,keyRshifted),10); // create key10



	keyLshifted = LeftShift(keyPF,'L',19);

	keyRshifted = LeftShift(keyPF,'R',19);

	keyPermutationA(JoinShifted(keyLshifted,keyRshifted),11); // create key11



	keyLshifted = LeftShift(keyPF,'L',21);

	keyRshifted = LeftShift(keyPF,'R',21);

	keyPermutationA(JoinShifted(keyLshifted,keyRshifted),12); // create key12



	keyLshifted = LeftShift(keyPF,'L',23);

	keyRshifted = LeftShift(keyPF,'R',23);

	keyPermutationA(JoinShifted(keyLshifted,keyRshifted),13); // create key13



	keyLshifted = LeftShift(keyPF,'L',25);

	keyRshifted = LeftShift(keyPF,'R',25);

	keyPermutationA(JoinShifted(keyLshifted,keyRshifted),14); // create key14



	keyLshifted = LeftShift(keyPF,'L',27);

	keyRshifted = LeftShift(keyPF,'R',27);

	keyPermutationA(JoinShifted(keyLshifted,keyRshifted),15); // create key15



	keyLshifted = LeftShift(keyPF,'L',28);

	keyRshifted = LeftShift(keyPF,'R',28);

	keyPermutationA(JoinShifted(keyLshifted,keyRshifted),16); // create key16

#endif

}
des.h
[/PHP]

[PHP]// DES.h: interface for the CDES class.

//

//////////////////////////////////////////////////////////////////////



#if !defined(AFX_DES_H__73DFD70F_BB37_4FD4_942C_54906CE719A1__INCLUDED_)

#define AFX_DES_H__73DFD70F_BB37_4FD4_942C_54906CE719A1__INCLUDED_



#if _MSC_VER > 1000

#pragma once

#endif // _MSC_VER > 1000



#define DES



#ifdef SDES

	#define KEY_TOTAL_LENGTH 10

	#define KEY_USED_BITS 10

	#define NO_OF_KEYS 2

	#define KEY_P_LENGTH 8

	#define DATA_LENGTH 8

	#define SROWS 4

	#define SCOLS 4

	#define NO_OF_S 2

#else if defined DES

	#define KEY_TOTAL_LENGTH 64

	#define KEY_USED_BITS 56

	#define NO_OF_KEYS 16

	#define KEY_P_LENGTH 48

	#define DATA_LENGTH 64

	#define SROWS 4

	#define SCOLS 16

	#define NO_OF_S 8

#endif





class CDES  

{

public:

	char* Decrypt();

	char* Encrypt();

	CDES(char* data, char* key);

	virtual ~CDES();



private:

	void GenKeys();

	char* PermuteSres_DES(char*);

	char* JoinSres_DES(char*,char*,char*,char*,char*,char*,char*,char*);

	void FillS7_DES();

	void FillS6_DES();

	void FillS5_DES();

	void FillS4_DES();

	void FillS3_DES();

	void FillS2_DES();

	void FillS1_DES();

	void FillS0_DES();

	void FillAllS();

	char* IPInverse(char*);

	char* Switch(char*);

	char* FKFunction(char*,int);

	char* FKFinal(char*,char*);

	char* XORLandP(char*,char*);

	void print(char*,int);

	void SampleKeys();

	char* PermuteSres(char*);

	char* JoinSres(char*,char*);

	char* Bin2bit(int);

	char* Bin4bit(int);

	int Dec2bit(char,char);

	int Dec4bit(char,char,char,char);

	int GetValue(int,int,int);

	char* GetSValue(char*,int);

	void FillS1_SDES();

	void FillS0_SDES();

	char XOR(char,char);

	char* XORwithKey(char*,int);

	char* ExtendedPermutation(char*);

	char* DataIP();

	char* DataIP_DES();

	void keyPermutationA(char*,int);

	char* JoinShifted(char*,char*);

	char* LeftShift(char*, char, int);

	char* keyIPermutation();

	char data[DATA_LENGTH];

	char Compkey[KEY_TOTAL_LENGTH];



	char key[NO_OF_KEYS][KEY_P_LENGTH];



	int S[NO_OF_S][SROWS][SCOLS];

};



#endif // !defined(AFX_DES_H__73DFD70F_BB37_4FD4_942C_54906CE719A1__INCLUDED_)
[/PHP]

i can't compile this program to be application.please help

---

### Post by monkeyking on 2009-03-05
post your  compile errors, after using 
-Wall -g

---

### Post by AlexenderReez on 2009-03-05
> **monkeyking said:**
> post your  compile errors, after using 
-Wall -g

> [ reez @ alexendeRReez : /home/reez/Desktop/DES ] g++ -c '/home/reez/Desktop/DES/DES.cpp'
/home/reez/Desktop/DES/DES.cpp:4:22: error: iostream.h: No such file or directory
In file included from /home/reez/Desktop/DES/DES.cpp:8:
/home/reez/Desktop/DES/DES.h:23:7: warning: extra tokens at end of #else directive
/home/reez/Desktop/DES/DES.cpp:1061:7: warning: extra tokens at end of #else directive
/home/reez/Desktop/DES/DES.cpp: In constructor ‘CDES::CDES(char*, char*)’:
/home/reez/Desktop/DES/DES.cpp:21: error: ‘cout’ was not declared in this scope
/home/reez/Desktop/DES/DES.cpp:21: error: ‘endl’ was not declared in this scope
/home/reez/Desktop/DES/DES.cpp: In member function ‘char* CDES::Encrypt()’:
/home/reez/Desktop/DES/DES.cpp:47: error: ‘cout’ was not declared in this scope
/home/reez/Desktop/DES/DES.cpp:47: error: ‘endl’ was not declared in this scope
/home/reez/Desktop/DES/DES.cpp: In member function ‘int CDES::GetValue(int, int, int)’:
/home/reez/Desktop/DES/DES.cpp:620: error: ‘cout’ was not declared in this scope
/home/reez/Desktop/DES/DES.cpp:620: error: ‘endl’ was not declared in this scope
/home/reez/Desktop/DES/DES.cpp: In member function ‘char* CDES::Bin2bit(int)’:
/home/reez/Desktop/DES/DES.cpp:676: warning: deprecated conversion from string constant to ‘char*’
/home/reez/Desktop/DES/DES.cpp:678: warning: deprecated conversion from string constant to ‘char*’
/home/reez/Desktop/DES/DES.cpp:680: warning: deprecated conversion from string constant to ‘char*’
/home/reez/Desktop/DES/DES.cpp:682: warning: deprecated conversion from string constant to ‘char*’
/home/reez/Desktop/DES/DES.cpp: In member function ‘char* CDES::Bin4bit(int)’:
/home/reez/Desktop/DES/DES.cpp:688: warning: deprecated conversion from string constant to ‘char*’
/home/reez/Desktop/DES/DES.cpp:690: warning: deprecated conversion from string constant to ‘char*’
/home/reez/Desktop/DES/DES.cpp:692: warning: deprecated conversion from string constant to ‘char*’
/home/reez/Desktop/DES/DES.cpp:694: warning: deprecated conversion from string constant to ‘char*’
/home/reez/Desktop/DES/DES.cpp:696: warning: deprecated conversion from string constant to ‘char*’
/home/reez/Desktop/DES/DES.cpp:698: warning: deprecated conversion from string constant to ‘char*’
/home/reez/Desktop/DES/DES.cpp:700: warning: deprecated conversion from string constant to ‘char*’
/home/reez/Desktop/DES/DES.cpp:702: warning: deprecated conversion from string constant to ‘char*’
/home/reez/Desktop/DES/DES.cpp:704: warning: deprecated conversion from string constant to ‘char*’
/home/reez/Desktop/DES/DES.cpp:706: warning: deprecated conversion from string constant to ‘char*’
/home/reez/Desktop/DES/DES.cpp:708: warning: deprecated conversion from string constant to ‘char*’
/home/reez/Desktop/DES/DES.cpp:710: warning: deprecated conversion  [ 08:01:29 ]onstant to ‘char*’
/home/reez/Desktop/DES/DES.cpp:712: warning: deprecated conversion from string constant to ‘char*’
/home/reez/Desktop/DES/DES.cpp:714: warning: deprecated conversion from string constant to ‘char*’
/home/reez/Desktop/DES/DES.cpp:716: warning: deprecated conversion from string constant to ‘char*’
/home/reez/Desktop/DES/DES.cpp:718: warning: deprecated conversion from string constant to ‘char*’
/home/reez/Desktop/DES/DES.cpp: In member function ‘void CDES::print(char*, int)’:
/home/reez/Desktop/DES/DES.cpp:776: error: ‘cout’ was not declared in this scope
/home/reez/Desktop/DES/DES.cpp:776: error: ‘endl’ was not declared in this scope
/home/reez/Desktop/DES/DES.cpp: In member function ‘char* CDES::FKFunction(char*, int)’:
/home/reez/Desktop/DES/DES.cpp:820: error: ‘cout’ was not declared in this scope
/home/reez/Desktop/DES/DES.cpp:820: error: ‘endl’ was not declared in this scope
/home/reez/Desktop/DES/DES.cpp: In member function ‘char* CDES::Decrypt()’:
/home/reez/Desktop/DES/DES.cpp:1022: error: ‘cout’ was not declared in this scope
/home/reez/Desktop/DES/DES.cpp:1022: error: ‘endl’ was not declared in this scope


> [ reez @ alexendeRReez : /home/reez/Desktop/DES ] g++  '/home/reez/Desktop/DES/main.cpp' -Wall -g -o des
/home/reez/Desktop/DES/main.cpp:1:22: error: iostream.h: No such file or directory
In file included from /home/reez/Desktop/DES/main.cpp:5:
/home/reez/Desktop/DES/DES.h:23:7: warning: extra tokens at end of #else directive
/home/reez/Desktop/DES/main.cpp:13: error: ‘::main’ must return ‘int’
/home/reez/Desktop/DES/main.cpp: In function ‘int main()’:
/home/reez/Desktop/DES/main.cpp:24: error: ‘cout’ was not declared in this scope
/home/reez/Desktop/DES/main.cpp:24: error: ‘endl’ was not declared in this scope
/home/reez/Desktop/DES/main.cpp:25: error: ‘cin’ was not declared in this scope
/home/reez/Desktop/DES/main.cpp:27: error: ‘tolower’ was not declared in this scope
/home/reez/Desktop/DES/main.cpp: In function ‘char* Binary(char)’:
/home/reez/Desktop/DES/main.cpp:176: warning: deprecated conversion from string constant to ‘char*’
/home/reez/Desktop/DES/main.cpp:178: warning: deprecated conversion from string constant to ‘char*’
/home/reez/Desktop/DES/main.cpp:180: warning: deprecated conversion from string constant to ‘char*’
/home/reez/Desktop/DES/main.cpp:182: warning: deprecated conversion from string constant to ‘char*’
/home/reez/Desktop/DES/main.cpp:184: warning: deprecated conversion from string constant to ‘char*’
/home/reez/Desktop/DES/main.cpp:186: warning: deprecated conversion from string constant to ‘char*’                                                 [ 08:03:05 ]
/home/reez/Desktop/DES/main.cpp:188: warning: deprecated conversion from string constant to ‘char*’
/home/reez/Desktop/DES/main.cpp:190: warning: deprecated conversion from string constant to ‘char*’
/home/reez/Desktop/DES/main.cpp:192: warning: deprecated conversion from string constant to ‘char*’
/home/reez/Desktop/DES/main.cpp:194: warning: deprecated conversion from string constant to ‘char*’
/home/reez/Desktop/DES/main.cpp:196: warning: deprecated conversion from string constant to ‘char*’
/home/reez/Desktop/DES/main.cpp:198: warning: deprecated conversion from string constant to ‘char*’
/home/reez/Desktop/DES/main.cpp:200: warning: deprecated conversion from string constant to ‘char*’
/home/reez/Desktop/DES/main.cpp:202: warning: deprecated conversion from string constant to ‘char*’
/home/reez/Desktop/DES/main.cpp:204: warning: deprecated conversion from string constant to ‘char*’
/home/reez/Desktop/DES/main.cpp:206: warning: deprecated conversion from string constant to ‘char*’
/home/reez/Desktop/DES/main.cpp:208: warning: deprecated conversion from string constant to ‘char*’


please help!

---

