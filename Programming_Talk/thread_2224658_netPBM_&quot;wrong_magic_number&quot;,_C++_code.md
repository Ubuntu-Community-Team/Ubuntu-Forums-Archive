---
title: "netPBM &quot;wrong magic number&quot;, C++ code"
date: 2014-05-17
forum: Programming Talk
---

### Post by male2 on 2014-05-17
Hello,
i have a problem with my code. I am supposed to write a program using netPBM which:
rotates image, uses interpolation to fill holes in image, stretches image to make sure it fits after being rotated, converts colorful image to monochromatic one, aligns histogram.
I wrote it, I am able to compile it, I run it with image, later I receive pgm image as output. I want to convert pgm to jpeg, and there is "wrong magic number, not a pgm file". What am I doing wrong?

```
#include <pgm.h>
#include <stdio.h>
#include <math.h>




gray **tabWe, **tabWy;
int szer, wys;
gray maxVal;
FILE *in,*out;


void menu();
void globHist();
void lokalHist();
void obrot();
void liczHist(int *hist,int granica_dw, int granica_dh, int granica_gw, int granica_gh);
void dystrybuanta(double *rozk_praw, double *dyst, int *hist, int granica_gw, int granica_gh, int max, int min);
void LUT(int *lut,double *zrod,int klasy, int min, int max);
void histeq(int kl, int max, int *lut,int granica_dw, int granica_dh, int granica_g_, int granica_gh);
void *znajdzMinMax(int *min, int *max, int sx, int sy, int blok);
void zwolnijPamiec(int *hist, double *rozk_praw, double *dyst, int *lut);
void zeruj(int *tab, int max);
void zerujD(double *tab, int max);
void interpolacja(gray **tab, int wys, int szer);


int main(int argc, char *argv[]) {
	if (argc !=3) {
		printf("Aby uruchomic program nalezy wywolac go poleceniem:\n-nazwe pliku wejsciowego\n-nazwe pliku wyjsciowego\n");
		printf("np. %s input.bmp output.bmp\n",argv[0]);
		exit(-1);
	}
	in = fopen(argv[1],"rb");
	if(in == NULL)
		printf("Blad otwarcia pliku!");
	tabWe = pgm_readpgm(in,&szer,&wys,&maxVal);
	fclose(in);
	printf("Informacje o obrazie:\n");
	printf("Szerokosc: %d\nWysokosc: %d\nMax val: %d\n",szer,wys,maxVal);
        out = fopen(argv[2],"wb");
	if(out == NULL)
		printf("Blad otwarcia pliku!");
	printf("Utworzono plik wyjsciowy!\n");
	menu();
	getchar();	
	return 0;
}


void menu() {
		int opcja;
		printf("Opcje:\n");
		printf("1. Globalne wyrownanie histogramu dla podanej ilosci klas\n");
		printf("2. Lokalne wyrownanie histogramu dla podanej ilosci klas\n");
		printf("3. Obrot obrazu o podany kat\n");
		printf("Wybrano: ");
		scanf("Wybor: %d",&opcja);
		switch(opcja) {
			case 1:
				globHist();
				break;
			case 2:
				lokalHist();
				break;
			case 3:
				obrot();
				break;
			default:
				break;
		}
}


void globHist() {
	int klasy=0,kl,k;
	int potegi[] = {1,2,4,8,16,32,64,128,256};
	printf("Podaj ilosc klas (wartosc musi byc potega dwujki nie wieksza niz 256):\n");
	scanf("%d",&kl);
	for(k=0;k<10;k++) {
		if(kl == potegi[k]) {
			klasy = potegi[k];
			break;
		}
	}
	if(klasy == 0) {
		printf("Ilosc klas MUSI byc potega dwujki nie wieksza niz 256!\n");
		exit(-1);
	}
	int *hist = (int *)malloc((maxVal+1)*sizeof(int));
	double *rozk_praw = (double*)malloc((maxVal+1)*sizeof(double));
	double *dyst = (double *)malloc((maxVal+1)*sizeof(double));
	int *lut = (int *)malloc((maxVal+1)*sizeof(int));
	
	zeruj(hist, maxVal+1);
	zeruj(lut, maxVal+1);
	zerujD(rozk_praw, maxVal+1);
	zerujD(dyst, maxVal+1);		
	liczHist(hist,0,0,szer,wys);
	dystrybuanta(rozk_praw,dyst,hist, szer, wys, maxVal, 0);
	LUT(lut,dyst,klasy,0,maxVal);
	tabWy = pgm_allocarray(szer, wys);
	
	histeq(klasy,maxVal,lut,0,0,szer,wys);
	pgm_writepgm(out, tabWy, szer, wys, maxVal, 0);
	zwolnijPamiec(hist,rozk_praw,dyst,lut);
	fclose(out);
	printf("Wyrownano histogram globalnie.\n");
}


void liczHist(int *hist,int granica_dw, int granica_dh, int granica_gw, int granica_gh) {
	int k,z;


	for(k=granica_dh;k<granica_gh;k++) {
		for(z=granica_dw;z<granica_gw;z++) {
			hist[tabWe[k][z]]++;
		}	
	}
}


void dystrybuanta(double *rozk_praw, double *dyst, int *hist, int granica_gw, int granica_gh, int max, int min) {
	int k,z;
	double l_pikseli = granica_gw * granica_gh;


	for(k=min; k<=max; k++)
		rozk_praw[k] = (double)hist[k]/(double)l_pikseli;
	
	for(k=0; k<=max; k++)
		for(z=0; z<=k; z++)
			dyst[k] += rozk_praw[z];
}


void LUT(int *lut,double *zrod,int klasy, int min, int max) {
	int k;
	double first_nd;


	for(k=0;k<max+1;k++) {
		if(zrod[k]>0.0000000001) {
			first_nd = zrod[k];
			break;
		}
	}
	for(k=min;k<max+1;k++) {
		lut[k] =round(((zrod[k] - first_nd)/(1.0-first_nd))*(klasy-1));
	}	
}


void histeq(int kl, int max,int *lut,int granica_dw, int granica_dh, int granica_gw, int granica_gh) {
	int k,z,temp;


	for(k=granica_dh;k<granica_gh;k++)
		for(z=granica_dw;z<granica_gw;z++) {
			temp = lut[ tabWe[k][z] ]*(((double)max+1.0)/((double)kl-1));
			if(temp > 255)
				tabWy[k][z] = 255;
			else
				tabWy[k][z] = temp;
		}	
}
void lokalHist() {
	int blok,k,z;
	tabWy = pgm_allocarray(szer, wys);
	int *hist, *lut;
	double *rozk_praw, *dyst;
	int klasy = 64;
	double krok_x, krok_y;
	int min, max;
	printf("Wybierz podzia&#322; na bloki:\n1. 16x16\n2. 32x32\n" );
	scanf("%d",&blok);
	switch(blok) {
			case 1:
				blok = 16;
				break;
			case 2:
				blok = 32;
				break;
	}
	krok_x = (double)szer/(double)blok;
	krok_y = (double)wys/(double)blok;
	printf("Klasy: %d, blok: %dx%d\n",klasy,blok,blok);
	sleep(1);
	FILE *plik;
	plik = fopen("min_max.txt","w");
	for(k=1;k<=krok_y;k++) {
		for(z=1;z<=krok_x;z++) {
		  znajdzMinMax(&min, &max, k, z, blok);
		  fprintf(plik,"minimum: %d, maksimum: %d\n",min,max);
			hist = (int *)malloc((max+1)*sizeof(int));
			rozk_praw = (double*)malloc((max+1)*sizeof(double));
			dyst = (double *)malloc((max+1)*sizeof(double));
			lut = (int *)malloc((max+1)*sizeof(int));
			zeruj(hist, max+1);
			zeruj(lut, max+1);
			zerujD(rozk_praw, max+1);
			zerujD(dyst, max+1);
			
			liczHist(hist,blok*(z-1),blok*(k-1),z*blok,k*blok);
			dystrybuanta(rozk_praw,dyst,hist, blok, blok, max, min);
			LUT(lut,dyst,klasy,min,max);
			histeq(klasy,max,lut,blok*(z-1),blok*(k-1),z*blok,k*blok);
			
			zwolnijPamiec(hist,rozk_praw,dyst,lut);
		}	
	}
	pgm_writepgm(out, tabWy, szer, wys, maxVal, 0);
	fclose(out);
	printf("Wyrownano histogram lokalnie.\n");
}
void *znajdzMinMax(int *min, int *max, int s_x, int s_y, int blok) {
	int i,j;
	*min = tabWe[blok*(s_x-1)][blok*(s_y-1)];
	*max = tabWe[blok*(s_x-1)][blok*(s_y-1)];
	for(j=blok*(s_x-1); j<blok*s_x; j++) {
		for(i=blok*(s_y-1); i<blok*s_y; i++) {
			if(tabWe[j][i] > *max)
				*max = tabWe[j][i];
			if(tabWe[j][i] < *min)
				*min = tabWe[j][i];
		}
	}
}
void zeruj(int *tab, int max) {
	int i;
	for(i=0; i < max; i++) {
		tab[i] = 0;
	}
}
void zerujD(double *tab, int max) {
	int i;
	for(i=0; i < max; i++) {
		tab[i] = 0;
	}
}
void zwolnijPamiec(int *hist, double *rozk_praw, double *dyst, int *lut) {
	free(hist);
	free(rozk_praw);
	free(dyst);
	free(lut);
}
void interpolacja(gray **tab, int wys, int szer) {
	int i,j;
	for(j=1; j<wys-1; j++) {
		for(i=1; i<szer-1; i++) {
			if(tab[j][i]==0) {
				tab[j][i] = (int)(tab[j-1][i]+tab[j+1][i]+tab[j][i-1]+tab[j][i+1])/4;
			}
		}
	}
}
void obrot() {
	gray **temp;
	double kat,px,py;;
	int x,y,nowa_szer,nowa_wys;
	double NewX, NewY;
	printf("Podaj kat obrotu obrazu (w stopniach)\n");
	scanf("%lf",&kat);
	printf("Podano kat: %lf\n",kat);
	double rad_kat = 3.14*kat/180;


	double ss = sin(rad_kat);
	double cs = cos(rad_kat);


	nowa_szer =abs(wys*cs) + abs(szer*ss)+450;
	nowa_wys = abs(szer*cs) + abs(wys*ss)+450;
	printf("nowa_szer = %d, nowa_wys = %d\n",nowa_szer,nowa_wys);
	tabWy = pgm_allocarray(nowa_szer, nowa_wys);
	temp = pgm_allocarray(nowa_szer, nowa_wys);
	double xcenter = (double)(nowa_szer)/2.0;   
	double ycenter = (double)(nowa_wys)/2.0;
	
	int dx = (nowa_szer - szer)/2;
	int dy = (nowa_wys - wys)/2;
	for (y=0; y < wys; y++) {
   		for (x=0; x < szer; x++) {
				temp[y+dy][x+dx] = tabWe[y][x];	
		}
	}
	int a,b;
	for (a = 0; a < nowa_wys; ++a) {
   		for (b = 0; b < nowa_szer; ++b) {
      		int rorig = (ycenter + ((double)(a)-ycenter)*cs - ((double)(b)-xcenter)*ss);
      		int corig = (xcenter + ((double)(a)-ycenter)*ss + ((double)(b)-xcenter)*cs);
      		
      		if (rorig >= 0 && rorig < nowa_wys && corig >= 0 && corig < nowa_szer) {
         			tabWy[rorig][corig] = temp[a][b];
      		}
     		else
      				continue;
   		}
	}
	interpolacja(tabWy,nowa_wys,nowa_szer);
	pgm_writepgm(out, tabWy, nowa_szer, nowa_wys, maxVal, 0);
	fclose(out);
	printf("Pomyslnie obrocono obraz.\n"); 
}
```

---

### Post by whitesmith on 2014-05-17
Are you asking for help with a homework assignment? Sorry, we don't do that. The issue relates to C++ and should be posted elsewhere.

---

### Post by bapoumba on 2014-05-17
*Thread moved to **Programming Talk**.* And closed

---

