---
title: "A Canasta Game that the computer cannot win."
date: 2011-07-15
forum: Programming Talk
---

### Post by machdohvah on 2011-07-15
Hello all --

This is my first thread here, so please bare with me. I have created a Canasta card game in Borland C++ using dosbox and Ubuntu 10.10. My current problem is that the computer never wins. I have been struggling with it for many years. Any help would be appreciated.

```

#define PROGNAME "GCANASTA"
#define VERSION "15Jul2011"
#define AUTHOR "Michael Flower"

/*

New program (rendered here) ...

GCANASTA.CPP graphic version with entire re-write.

24Nov2007 This started life as a character based system with mouse
attached. That program had too many bugs in it.

26Jan2008 Finished a working game with computer player logic.

29Aug2009 Corrected ComputerTurn to check EndRound at beginning.

30Aug2009 Corrected errors in ComputerTurn.

31Aug2009 There are several problems. Something in ComputerTurn is now
producing an endless loop and I counted ten sevens during play. Nasty!
Decided to remove the DOS SORT calls and replace them with qsort. The
computer locks up when player takes successfully on the first move.

01Sep2009 Tried to OVERLAY this thing but have yet to produce an OVR file.
The computer hand is corrupted upon melding. It appearently is erasing the
wrong cards after it melds the correct ones. Bug corrected: incorrect index
reference.

06Sep2009 Removed all penalties in figuring the score.

12Sep2009 Moved the Meld menu to left edge. Added Save and Restore.

31Oct2010 Reprogrammed the menus.

07Nov2010 Removed conditional on cOutCapabile.

08Nov2010 Changed condition from <= 2 to < 1. gpMeldedBefore and
gcMeldedBefore cancelled between rounds.

14Jul2011 Removed all "far" references as I started to compile this
again in "dosbox" in root terminal with Ubuntu 10.10 operating system.
Introduced NUMBER_CANASTA_OUT, NUMBER_CARDS_DRAW, gpHandCardCount,
and gcHandCardCount. Corrected problem of one card in hand left with
respect to NUMBER_CANASTA_OUT during discard. Created pCalcFirstMeld
on Status Line.

15Jul2011 Returned "far" references to data and functions for it was
over-running its memory. Affixed initials before local variable for
garrentee of seperation. g- = global.


  NOTE: All rules of Canasta in Hoyle are followed. This is the Two-Hand
Canasta variation. "Hoyle's Rules of Games" by Albert H Morehead and
Geoffrey Mott-Smith, revised and updated by Philip D Morehead, Dec2001
edition, page 140.

The definition of TESTING is only needed while debugging the program.
The definition of USE_MOUSE is only needed if the mouse is needed.

*/

#define TESTING
// #define USE_MOUSE

#include <conio.h>
#include <ctype.h>
#include <graphics.h>
#include <stdarg.h>
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <time.h>

/*

Compile with "MLFMOUSE.CPP". This program uses the mouse object
developed purely from interrupts in assembly code. "MouseInfo"
structure is included there.

*/

#ifdef USE_MOUSE
#include "mlfmouse.h"
struct MouseInfo gMouseInformation = { 0, 0, 0, 0, 0 };
#endif

#define DECK_SIZE 108
#define DESKTOP_BUTTON_COUNT 6
#define DISCARD_PULLDOWN_COUNT 15
#define EMPTY -1
#define GAME_PULLDOWN_COUNT 1
#define HELP_PULLDOWN_COUNT 1
#define MAX_ROUNDS 8
#define MELD_DEPTH 15
#define MELD_LOCATIONS 12
#define MELD_PULLDOWN_COUNT 15
#define NATURAL_RANK_PULLDOWN_COUNT 11
#define NUMBER_CANASTA_OUT 2
#define NUMBER_CARDS_DRAW 2
#define STATUS_FOR 14
#define STATUS_BACK 6
#define STATUS_LINE 59
#define STOCK_COLUMN 30
#define STOCK_ROW 24

/*

Eventually, these two will be the current directory.

*/

#define PATH_TO_BGI "\\TC\\BGI"
// #define PATH_TO_BGI ""
#define PATH_TO_CARDS "\\MYDOCS\\TC\\CARDS\\PXL\\"
// #define PATH_TO_CARDS ""

enum {COMPUTER, PLAYER, NUM_PLAYERS};
enum bool {false, true};

/*

Cards are shuffled in this program by sorting on random numbers. The
Title field is only two characters long. Rank and Suit are needed for
sorting the hands. Rank is a number that is in line with its rank in
the game while Title contains the name of the card. This seperation is
needed for the jokers. All arrays with +1 allocation are there for
avoiding sort aliocation errors.

*/

class cCard {
public:
  char Shuffle[4], Title[3], Rank, Suit;
  int Value;
  bool IsWild;
};

cCard far gCard[DECK_SIZE+1];

/*

New cards in the hand are placed at the end of the hand and later
sorted. The hand only holds the rank and the card index
for all the other information is static with the card itself.

*/

class cHand {
public:
  char Rank; // for sorting
  int Index;
  bool Selected;
};

cHand far gHand[NUM_PLAYERS+1][DECK_SIZE+1];

/*

All threes are in Meld0. Meld1 thru MELD_LOCATIONS is in order of
rank string minus the wild cards.

*/

class cMeld {
public:
  bool IsBook;
  bool HasWild;
  int Position[MELD_DEPTH+1];
};

cMeld far gMeld[NUM_PLAYERS+1][MELD_LOCATIONS+1];

/*

The desktop menu has two incarnations, one for each phase.

*/

class cMenu {
public:
  char letter;
  char *caption;
  int row1, col1, row2, col2;
};

cMenu far gDesktop[2][DESKTOP_BUTTON_COUNT+1] = {
  {
    {'t', " Take ",    0, 0, 0, 5},
    {'d', " Draw ",    0, 6, 0,11},
    {'s', " Save ",    0,12, 0,17},
    {'r', " Restore ", 0,18, 0,26},
    {'e', " Exit   ",  0,27, 0,34},
    {'h', " Help ",    0,74, 0,79}
  }, {
    {'m', " Meld ",    0, 0, 0, 5},
    {'d', " Discard ", 0, 6, 0,14},
    {'d', "      ",    0,15, 0,20},
    {'d', "         ", 0,21, 0,29},
    {'e', " Exit   ",  0,30, 0,37},
    {'h', " Help ",    0,74, 0,79}
  }
};

/*

The second choices are the only things in the pull-down.

*/

cMenu far gDiscardMenu[DISCARD_PULLDOWN_COUNT+1] = {
  {'3'," 3 Three ", 2, 6, 2,14},
  {'4'," 4 Four  ", 3, 6, 3,14},
  {'5'," 5 Five  ", 4, 6, 4,14},
  {'6'," 6 Six   ", 5, 6, 5,14},
  {'7'," 7 Seven ", 6, 6, 6,14},
  {'8'," 8 Eight ", 7, 6, 7,14},
  {'9'," 9 Nine  ", 8, 6, 8,14},
  {'t'," T Ten   ", 9, 6, 9,14},
  {'j'," J Jack  ",10, 6,10,14},
  {'q'," Q Queen ",11, 6,11,14},
  {'k'," K King  ",12, 6,12,14},
  {'a'," A Ace   ",13, 6,13,14},
  {'2'," 2 Two   ",14, 6,14,14},
  {'z'," Z Joker ",15, 6,15,14},
  {'x'," X DONE  ",16, 6,16,14}
};

cMenu far gMeldMenu[MELD_PULLDOWN_COUNT+1] = {
  {'3'," 3 Three ", 2, 1, 2, 9},
  {'4'," 4 Four  ", 3, 1, 3, 9},
  {'5'," 5 Five  ", 4, 1, 4, 9},
  {'6'," 6 Six   ", 5, 1, 5, 9},
  {'7'," 7 Seven ", 6, 1, 6, 9},
  {'8'," 8 Eight ", 7, 1, 7, 9},
  {'9'," 9 Nine  ", 8, 1, 8, 9},
  {'t'," T Ten   ", 9, 1, 9, 9},
  {'j'," J Jack  ",10, 1,10, 9},
  {'q'," Q Queen ",11, 1,11, 9},
  {'k'," K King  ",12, 1,12, 9},
  {'a'," A Ace   ",13, 1,13, 9},
  {'2'," 2 Two   ",14, 1,14, 9},
  {'z'," Z Joker ",15, 1,15, 9},
  {'x'," X DONE  ",16, 1,16, 9}
};

cMenu far gNatualRankMenu[NATURAL_RANK_PULLDOWN_COUNT+1] = {
  {'4'," 4 Four  ", 3, 6, 3,14},
  {'5'," 5 Five  ", 4, 6, 4,14},
  {'6'," 6 Six   ", 5, 6, 5,14},
  {'7'," 7 Seven ", 6, 6, 6,14},
  {'8'," 8 Eight ", 7, 6, 7,14},
  {'9'," 9 Nine  ", 8, 6, 8,14},
  {'t'," T Ten   ", 9, 6, 9,14},
  {'j'," J Jack  ",10, 6,10,14},
  {'q'," Q Queen ",11, 6,11,14},
  {'k'," K King  ",12, 6,12,14},
  {'a'," A Ace   ",13, 6,13,14}
};

cMenu far gHelpMenu[HELP_PULLDOWN_COUNT+1] = {
  {'a'," About GCANASTA ", 2,63, 2,78}
};

/*

Miscellanious globals

*/

int    gBonusPoints[MAX_ROUNDS+1][NUM_PLAYERS+1];
char * gCardBackFileName = "FILENAME.EXT";
bool   gChanged = true;
int    gDiscard[DECK_SIZE+1];
bool   gEndGame = false;
bool   gEndRound = false;
int    gLastCB = 0;
int    gMeldPoints[MAX_ROUNDS+1][NUM_PLAYERS+1];
int    gNextCardInStock = EMPTY;
int    gPhase = 0;
char * gRankString = "3456789TJQKA2Z";
int    gRounds = 1;
int    gScore[MAX_ROUNDS+1][NUM_PLAYERS+1];
int    gStock[DECK_SIZE+1];
char * gSuitString = "HDSC";
int    gTextHeight;
int    gTextWidth;
int    gTopPile;

int    gcCanastaCount = 0;
int    gpCanastaCount = 0;
int    gcHandCardCount = 0;
int    gpHandCardCount = 0;
bool   gcMeldedBefore = false;
bool   gpMeldedBefore = false;
bool   gBlack3PreviousTurn = false;
int    gNextAvailableMeldPit = 0;
int    gWildsOnTable = 0;
int    gKnatsOnTable = 0;
bool   gWildInDiscardPile = false;

char   gS[80] = "";
char   gRecord[DECK_SIZE][80];

/*

Function declarations (c- = computer; p- = player)

*/

void far Abort(int,char *);                // a01
void far About();                          // a02
int  far pCalcFirstMeld();                 // c02 (dont ask)
void far ComputerTurn();                   // c01
void far DeselectAllInHand(int);           // d01
void far cDiscard(int,int);                // d02
bool far pDiscard();                       // d03
void far DisplayCard(int,int,int,bool);    // d04
bool far cDraw();                          // d05
bool far pDraw();                          // d06
int  far DrawCard(int);                    // d07
void far FigureScore(int);                 // f01
int  far cFindBlackThree();                // f02
int  far cFindMeldPit(char);               // f03
int  far cFindNaturalLowCountRank();       // f04
int  far cFindWild();                      // f05
bool far cFirstMeld();                     // f06
void far GetPixelsFromFile(char *,int,int,bool); // g01
void far Gprintf(int,int,int,int,char *,...); // g02
void far HideMenu(cMenu *,int);            // h01
bool far IsRedThree(int,int);              // i01
char far pMeld(bool ForTake);              // m01
void far cMeldAllNaturals();               // m02
int  far cMinLegalMeld();                  // m03
bool far pMinLegalMeld(bool);              // m04
void far NextCardBack();                   // n01
void far cOutCapabile();                   // o01
char far ReadDesktop();                    // r01
char far ReadMenu(cMenu *,int);            // r02
void far Refresh();                        // r03
void far RestoreBehindWindow(char *,int,int,int,int); // r04
void far RestoreStateOfComputer();         // r05
void far SaveBehindWindow(char *,int,int,int,int); // s01
void far SaveStateOfComputer();            // s02
int  far SelectCardInHand(int,char);       // s03
void far ShowMelds(int,int);               // s04
void far ShowMenu(cMenu *,int);            // s05
void far ShowScore();                      // s06
void far ShuffleDeck();                    // s07
void far SortHand(int);                    // s08
void far StartOver();                      // s09
bool far pTake();                          // t01
bool far cTryTakeDiscard();                // t02
void far WaitASec();                       // w01
int  far cWhereInHand(int);                // w02

void far ProgramConstructor();             // p01
bool far MainLoop();                       // m05
void far ProgramDestructor();              // p02
void far pd2();                            // p03

int  far sort_function( const void *, const void *); // s10

/*

Program entry point. Calls the constructor, maintains the main loop,
and then calls the destructor.

*/

void main() {
  ProgramConstructor();
  while (MainLoop());
  ProgramDestructor();
}

/*

This function alerts the user what line called the function and for
what reason, calls the destructor, then aborts the program.

*/

void far Abort(int a01L, char *a01S) {
  cleardevice();
  Gprintf(1,1,YELLOW,BLACK,"%s aborted on line %d for this reason:",
    PROGNAME,a01L);
  Gprintf(2,1,YELLOW,BLACK,"%s",a01S);
  Gprintf(3,1,YELLOW,BLACK,"Press a key to continue...");
  getch();
  ProgramDestructor();
}

/*

This function shows a window that shows an announcement of information
about the program.

*/

void far About() {
  int a02I=0;

  SaveBehindWindow("ABTSAVE.DTA",25,26,38,54);
  Gprintf(25,26, BLACK, WHITE, "ÚÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄ¿");
  Gprintf(26,26, BLACK, WHITE, "³ %s                 ³%c",PROGNAME,
    0xB2);
  Gprintf(27,26, BLACK, WHITE, "³ %s                ³%c", VERSION,
    0xB2);
  Gprintf(28,26, BLACK, WHITE, "ÃÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄŽ%c",0xB2);
  Gprintf(29,26, BLACK, WHITE, "³ This program was written ³%c",0xB2);
  Gprintf(30,26, BLACK, WHITE, "³ by %s        ³%c",AUTHOR,0xB2);
  Gprintf(31,26, BLACK, WHITE, "³ and is intended as a     ³%c",0xB2);
  Gprintf(32,26, BLACK, WHITE, "³ demonstraion only and is ³%c",0xB2);
  Gprintf(33,26, BLACK, WHITE, "³ not for sale or lease to ³%c",0xB2);
  Gprintf(34,26, BLACK, WHITE, "³ anyone.                  ³%c",0xB2);
  Gprintf(35,26, BLACK, WHITE, "ÃÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄŽ%c",0xB2);
  Gprintf(36,26, BLACK, WHITE, "³ For the rules, see Hoyle ³%c",0xB2);
  Gprintf(37,26, BLACK, WHITE, "ÀÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÙ%c",0xB2);
  for (a02I=27;a02I<=54;a02I++) {
    Gprintf(38, a02I, BLACK, WHITE, "%c",0xB2);
  }
  ReadDesktop();
  RestoreBehindWindow("ABTSAVE.DTA",25,26,38,54);
}

/*

This function simulates the opponent player. It looks for a black
three, remembers if there was a black three in the previous turn and if
the discard pile has been taken in this turn. Depending on the result,
it tries to take the discard pile. Failing to take the discard pile, he
draws two cards. Depending on if he was finished with the previous
black three, he melds all the naturals he can. He checks to see if he
is capable to "go out". He checks for a first meld. He looks for a
black three, a wild, or a natural to discard ending his turn.

*/

void far ComputerTurn() {
  int c01BlackThree = EMPTY;
  bool c01ComputerTake = false;
  int c01Wild = EMPTY;
  int c01DeckIndex = 0;

  if (gEndRound) return;
  Refresh();
  c01BlackThree = cFindBlackThree();
  if (!gBlack3PreviousTurn) {
    if (cTryTakeDiscard()) {
      c01ComputerTake = true;
    }
  }
  if (!c01ComputerTake) {
    if (cDraw()) {
      gBlack3PreviousTurn = false;
    }
  }
  if ( !gcMeldedBefore ) gcMeldedBefore = cFirstMeld();
  if (gcMeldedBefore) cMeldAllNaturals();
// 07Nov2010 Removed conditional on cOutCapabile.
  cOutCapabile();
  c01Wild = cFindWild();
  if ( c01BlackThree != EMPTY ) {
    c01DeckIndex = c01BlackThree;
    cDiscard( c01DeckIndex, cWhereInHand( c01DeckIndex ));
    gBlack3PreviousTurn = true;
  }
  else {
    if ( !(gBlack3PreviousTurn) && !(gWildInDiscardPile) && (c01Wild != EMPTY) ) {
      c01DeckIndex = c01Wild;
      cDiscard( c01DeckIndex, cWhereInHand( c01DeckIndex ));
      gWildInDiscardPile = true;
    }
    else {
      c01DeckIndex = cFindNaturalLowCountRank();
      cDiscard( c01DeckIndex, cWhereInHand( c01DeckIndex ));
    }
  }
  gPhase = 0;
}

/*

This function de-selects all the cards in the specified hand.

*/

void far DeselectAllInHand(int d01Who) {
  int d01I=0;

  for (;d01I<DECK_SIZE;d01I++)
    gHand[d01Who][d01I].Selected = false;
}

/*

This function discards specified card from specified location in
the computer hand.

*/

void far cDiscard( int d02Which, int d02Where  ) {
  if ( gcHandCardCount == 1)
    if ( gcCanastaCount < NUMBER_CANASTA_OUT ) return;

  gTopPile++;
  gDiscard[gTopPile] = d02Which;
  gHand[COMPUTER][d02Where ].Index = EMPTY;
  gHand[COMPUTER][d02Where ].Rank = '~';
  gHand[COMPUTER][d02Where ].Selected = false;
  gcHandCardCount--;
  SortHand(COMPUTER);
}

/*

This function checks for minimum/legal meld, waits on the user to
specify a card for discard from his hand, removes the card from the
hand, places the card in the discard pile, sorts the hand in order of
rank, and checks for an empty hand declairing the round over.

*/

bool far pDiscard() {
  char d03A = ' ';
  int d03C, d03H;

  d03C=d03H=0;
  if (!(pMinLegalMeld(false))) return false;
/*

14Jul2011 Special case: If there is only one card left, disallow if
there are less then the NUMBER_CANASTA_OUT.

*/
  if ( gpHandCardCount == 1)
    if ( gpCanastaCount < NUMBER_CANASTA_OUT ) return false;

  for (;;) {
    d03A = ReadMenu(gDiscardMenu,DISCARD_PULLDOWN_COUNT);
    if (d03A == 0x0D) return false;
    d03A = toupper(d03A);
    if (d03A == 'X') return false;
    d03C = SelectCardInHand(PLAYER,d03A);
    if (d03C != EMPTY) break;
  }
  d03H = gHand[PLAYER][d03C].Index;
  gHand[PLAYER][d03C].Index = EMPTY;
  gHand[PLAYER][d03C].Rank = '~';
  gHand[PLAYER][d03C].Selected = false;
  gpHandCardCount--;
  gTopPile++;
  gDiscard[gTopPile] = d03H;
  SortHand(PLAYER);
  if (gpHandCardCount <= 0) gEndRound = true;

  return true;
}

/*

This function displays the selected card at specified row and col. It
needs to know if it is sideways or not.

*/

void far DisplayCard( int d04Card, int d04Row, int d04Col, bool d04Sideways ) {
  sprintf( gS, "%s.PXL", gCard[d04Card].Title );
  GetPixelsFromFile( gS, d04Row, d04Col, d04Sideways );
}

/*

Computer draws NUMBER_CARDS_DRAW cards storing the index and rank. It
shows a card back for each card as it processes. It notifies the caller
if it failed to draw a card.

*/

bool far cDraw() {
  int d05C=0,d05I;

for (d05I=0;d05I<NUMBER_CARDS_DRAW;d05I++) {
  d05C = DrawCard(COMPUTER);
  if (d05C == EMPTY) return false;
  gHand[COMPUTER][DECK_SIZE-(1+d05I)].Index = d05C;
  gHand[COMPUTER][DECK_SIZE-(1+d05I)].Rank = gCard[d05C].Rank;
  gcHandCardCount++;
#ifdef TESTING
  DisplayCard(d05C,STOCK_ROW,STOCK_COLUMN-4+(2*d05I),false);
#else
  GetPixelsFromFile( gCardBackFileName, STOCK_ROW, STOCK_COLUMN-4+(2*d05I),
    false );
#endif
}

  SortHand(COMPUTER);
  WaitASec();

  return true;
}

/*

User draws NUMBER_CARDS_DRAW cards storing the index and rank. It shows
a card face for each card as it processes. It notifies the caller if it
failed to draw a card.

*/

bool far pDraw() {
  int d06C=0, d06I;

for (d06I=0;d06I<NUMBER_CARDS_DRAW;d06I++) {
  d06C = DrawCard(PLAYER);
  if (d06C == EMPTY) return false;
  gHand[PLAYER][DECK_SIZE-(1+d06I)].Index = d06C;
  gHand[PLAYER][DECK_SIZE-(1+d06I)].Rank = gCard[d06C].Rank;
  gpHandCardCount++;
  DisplayCard(d06C,STOCK_ROW,STOCK_COLUMN-4+(2*d06I),false);
}

  SortHand(PLAYER);
  WaitASec();

  return true;
}

/*

This function draws a card into the specified hand. It checks for an
empty stock pile, draws a card from stock, checks for red threes (Meld0
is for threes, red and black) drawing a replacement card if needed.

*/

int far DrawCard(int d07Who) {
  int d07Result;
  bool d07Continuing = true;

  d07Result=0;
  while (d07Continuing) {
    if (gNextCardInStock == EMPTY) return EMPTY;
    d07Continuing = false;
    d07Result = gStock[gNextCardInStock];
    gStock[gNextCardInStock] = EMPTY;
    gNextCardInStock--;
    if (IsRedThree(d07Who, d07Result)) d07Continuing = true;
  }
  return d07Result;
}

/*

This function figures the score at the end of the round. Awards bonus
points, awards meld points, subtracts sorted hand, storing the running
total.

*/

void far FigureScore(int f01R) {
  int f01C,f01I,f01J,f01K;

  f01C=f01I=f01J=f01K=0;
  for (f01I=0;f01I<NUM_PLAYERS;f01I++) {
    gBonusPoints[f01R][f01I] = 0;
    for (f01J=1;f01J<MELD_LOCATIONS;f01J++) {
      if (gMeld[f01I][f01J].IsBook) {
        if(gMeld[f01I][f01J].HasWild)
             gBonusPoints[f01R][f01I] += 300; // black canasta
        else gBonusPoints[f01R][f01I] += 500; // red canasta
      }
    }

    for (f01J=0,f01K=0;f01J<MELD_DEPTH;f01J++) { // count red threes
      f01C = gMeld[f01I][0].Position[f01J];
      if (f01C == EMPTY) {
        break;
      }
      if ((gCard[f01C].Title[1] == 'H') ||
          (gCard[f01C].Title[1] == 'D')) {
        f01K++;
      }
    }
    gBonusPoints[f01R][f01I] += (f01K*100); // red three award

    gMeldPoints[f01R][f01I] = 0; // figure meld points
    for (f01J=0;f01J<MELD_LOCATIONS;f01J++) {
      for (f01K=0;f01K<MELD_DEPTH;f01K++) {
        f01C = gMeld[f01I][f01J].Position[f01K];
        if (f01C == EMPTY) {
          break;
        }
        gMeldPoints[f01R][f01I] += gCard[f01C].Value;
      }
    }

    for (f01J=0;f01J<DECK_SIZE;f01J++) { // deduct for cards in hand
      f01C = gHand[f01I][f01J].Index;
      if (f01C == EMPTY) {
        if (f01J==0) { // award 100 for going out
          gBonusPoints[f01R][f01I] += 100;
        }
        break;
      }
      else {
        gMeldPoints[f01R][f01I] -= gCard[f01C].Value;
      }
    }

    gScore[f01R][f01I] = gBonusPoints[f01R][f01I] + gMeldPoints[f01R][f01I];
    if (f01R > 0) gScore[f01R][f01I] += gScore[f01R-1][f01I];
  }
  if (gScore[f01R][PLAYER]   >= 5000) gEndGame = true;
  if (gScore[f01R][COMPUTER] >= 5000) gEndGame = true;
  if (f01R >= MAX_ROUNDS-1)           gEndGame = true;
}

/*

This function looks for a black three in computer hand sorted in order
by rank. Returns EMPTY if failed.

*/

int far cFindBlackThree() {
  int f02I;
  int f02Result = EMPTY;
  int f02DeckIndex;
  char f02A,f02B;

  for (f02I=0; f02I<DECK_SIZE; f02I++) {
    f02DeckIndex = gHand[COMPUTER][f02I].Index;
    if ( f02DeckIndex == EMPTY ) break;
    f02A = gCard[f02DeckIndex].Title[0];
    f02B = gCard[f02DeckIndex].Title[1];
    if ( f02A == '3' ) {
      if ((f02B == 'S') || (f02B == 'C')) {
        f02Result = f02DeckIndex;
        break;
      }
    }
  }

  return f02Result;
}

/*

This function find an the right meld pit for the computer hand for a
given natural to meld. Returns EMPTY if not found.

*/

int far cFindMeldPit( char f03NatInMeld) {
  int f03I, f03J;
  char f03RankOfCardInList;
  int f03Result = EMPTY;
  int f03DeckIndex;

  gNextAvailableMeldPit = 0;
  gWildsOnTable = 0;
  gKnatsOnTable = 0;
  for (f03I=1; f03I<MELD_LOCATIONS; f03I++) {
    for ( f03J=0; f03J<MELD_DEPTH; f03J++ ) {
      f03DeckIndex = gMeld[COMPUTER][f03I].Position[f03J];
      if ( f03DeckIndex == EMPTY ) break;
      f03RankOfCardInList = gCard[f03DeckIndex].Title[0];
      if (( f03RankOfCardInList != 'Z' ) && ( f03RankOfCardInList != '2' )) {
        if ( f03NatInMeld == f03RankOfCardInList ) {
          f03Result = f03I;
          break;
        }
        else break;
      }
    }
    if ( f03Result != EMPTY ) break;
    if (( f03J == 0 && f03DeckIndex == EMPTY )) break;
  }
  if ( f03Result == EMPTY ) gNextAvailableMeldPit = f03I;
  else {
    for ( f03J=0; f03J<MELD_DEPTH; f03J++ ) {
      f03DeckIndex = gMeld[COMPUTER][f03Result].Position[f03J];
      if ( f03DeckIndex == EMPTY ) break;
      switch ( gCard[f03DeckIndex].Title[0] ) {
      case 'Z':
      case '2':
        gWildsOnTable++;
        break;
      default:
        gKnatsOnTable++;
      }
    }
  }

  return f03Result;
}

/*

This function finds the lowest rank and the lowest count of a natural
to discard from the computer hand.

*/

int far cFindNaturalLowCountRank() {
  int f04Result;
  int f04I, f04J;
  char f04RankOfCardInHand, *fnlcrPtr;
  int f04NatCount[11];
  int f04DeckIndex;

  for (f04I=0; f04I<11; f04I++) f04NatCount[f04I] = 0;
  for (f04I=0; f04I<DECK_SIZE; f04I++) {
    f04DeckIndex = gHand[COMPUTER][f04I].Index;
    if ( f04DeckIndex == EMPTY ) break;
    f04RankOfCardInHand = gCard[f04DeckIndex].Title[0];
    fnlcrPtr = strchr( gRankString, f04RankOfCardInHand );
    switch ( f04RankOfCardInHand ) {
    case 'Z':
    case '2':
    case '3':
      break;
    default:
      f04NatCount[(int) (fnlcrPtr-gRankString)-1]++;
    }
  }
  f04RankOfCardInHand = ' ';
  for ( f04I=1; f04I<=8; f04I++) {
    for ( f04J=0; f04J<11; f04J++ ) {
      if ( f04NatCount[f04J] == f04I ) {
        f04RankOfCardInHand = gRankString[f04J+1];
        break;
      }
    }
    if ( f04RankOfCardInHand != ' ' ) break;
  }
  for (f04I=0; f04I<DECK_SIZE; f04I++) {
    f04DeckIndex = gHand[COMPUTER][f04I].Index;
    if ( gCard[f04DeckIndex].Title[0] == f04RankOfCardInHand ) {
      f04Result = f04DeckIndex;
      break;
    }
  }

  return f04Result;
}

/*

This function looks for a wild in the computer hand.

*/

int far cFindWild() {
  char f05RankOfCardInList;
  int f05I;
  int f05Result = EMPTY;
  int f05DeckIndex;

  for (f05I=0; f05I<DECK_SIZE; f05I++) {
    f05DeckIndex = gHand[COMPUTER][f05I].Index;
    if ( f05DeckIndex == EMPTY ) break;
    f05RankOfCardInList = gCard[f05DeckIndex].Title[0];
    if (( f05RankOfCardInList == '2' ) ||
        ( f05RankOfCardInList == 'Z' )) {
      f05Result = f05DeckIndex;
      break;
    }
  }

  return f05Result;
}

/*

This function attempts to meld from the computer hand for the first
time.

*/

bool far cFirstMeld() {
  int f06CardList[20];
  int f06I, f06J, f06K;
  int f06NatCount[11];
  int f06NatList[8];
  int f06NatInList;
  char *f06Ptr;
  char f06RankOfCardInList;
  bool f06Result = false;
  int f06Score;
  int f06WildList[12];
  int f06WldInHand = 0;
  int f06DeckIndex;
  int f06MeldPit = 0;
  int f06MinMeld = cMinLegalMeld();

  for (f06I=0; f06I<20; f06I++) f06CardList[f06I] = EMPTY;
  for (f06I=0; f06I<11; f06I++) f06NatCount[f06I] = 0;
  for (f06I=0; f06I<8; f06I++) f06NatList[f06I] = EMPTY;
  for (f06I=0; f06I<12; f06I++) f06WildList[f06I] = EMPTY;
  for (f06I=0; f06I<DECK_SIZE; f06I++) {
    f06DeckIndex = gHand[COMPUTER][f06I].Index;
    if ( f06DeckIndex == EMPTY ) break;
    f06RankOfCardInList = gCard[f06DeckIndex].Title[0];
    f06Ptr = strchr( gRankString, f06RankOfCardInList );
    switch ( f06RankOfCardInList ) {
    case 'Z':
    case '2':
    case '3':
      break;
    default:
      f06NatCount[(int) (f06Ptr-gRankString)-1]++;
    }
  }
  f06RankOfCardInList = ' ';
  for ( f06I=8; f06I>=2; f06I--) {
    for ( f06J=10; f06J>=0; f06J-- ) {
      if ( f06NatCount[f06J] == f06I ) {
        f06RankOfCardInList = gRankString[f06J+1];
        f06Score = 0;
        f06NatInList = 0;
        for ( f06K=0; f06K<DECK_SIZE; f06K++ ) {
          f06DeckIndex = gHand[COMPUTER][f06K].Index;
          if ( f06DeckIndex == EMPTY ) break;
          if ( gCard[f06DeckIndex].Title[0] == f06RankOfCardInList ) {
            f06CardList[f06NatInList] = f06DeckIndex;
            f06NatList[f06NatInList++] = f06DeckIndex;
            f06Score += gCard[f06DeckIndex].Value;
            if ( f06Score >= f06MinMeld ) break;
          }
        }
        if ( f06Score >= f06MinMeld ) f06Result = true;
        else {
          f06Result = false;
          for ( f06K=0; f06K<DECK_SIZE; f06K++ ) {
            f06DeckIndex = gHand[COMPUTER][f06K].Index;
            if ( f06DeckIndex == EMPTY ) break;
            if ( gCard[f06DeckIndex].Title[0] == 'Z' ) {
              f06CardList[f06NatInList+f06WldInHand] = f06DeckIndex;
              f06WildList[f06WldInHand++] = f06DeckIndex;
              f06Score += gCard[f06DeckIndex].Value;
              if ( f06Score >= f06MinMeld ) {
                f06Result = true;
                break;
              }
            }
          }
          if ( !f06Result ) {
            for ( f06K=0; f06K<DECK_SIZE; f06K++ ) {
              f06DeckIndex = gHand[COMPUTER][f06K].Index;
              if ( f06DeckIndex == EMPTY ) break;
              if ( gCard[f06DeckIndex].Title[0] == '2' ) {
                f06CardList[f06NatInList+f06WldInHand] = f06DeckIndex;
                f06WildList[f06WldInHand++] = f06DeckIndex;
                f06Score += gCard[f06DeckIndex].Value;
                if ( f06Score >= f06MinMeld ) {
                  f06Result = true;
                  break;
                }
              }
            }
          }
          if ( f06NatInList <= f06WldInHand ) f06Result = false;
        }
        if ( f06Result ) break;
        else {
          f06NatInList = 0; f06WldInHand = 0;
          for ( f06K=0; f06K<20; f06K++ ) f06CardList[f06K] = EMPTY;
          for ( f06K=0; f06K<8; f06K++ ) f06NatList[f06K] = EMPTY;
          for ( f06K=0; f06K<12; f06K++ ) f06WildList[f06K] = EMPTY;
        }
      }
    }
    if ( f06Result ) break;
  }
  if ( f06Result ) {
    switch (f06RankOfCardInList) {
    case '4': f06MeldPit =  1; break;
    case '5': f06MeldPit =  2; break;
    case '6': f06MeldPit =  3; break;
    case '7': f06MeldPit =  4; break;
    case '8': f06MeldPit =  5; break;
    case '9': f06MeldPit =  6; break;
    case 'T': f06MeldPit =  7; break;
    case 'J': f06MeldPit =  8; break;
    case 'Q': f06MeldPit =  9; break;
    case 'K': f06MeldPit = 10; break;
    case 'A': f06MeldPit = 11; break;
    }
    for ( f06J=0; f06J<f06WldInHand; f06J++ ) {
      f06DeckIndex = f06WildList[f06J];
      if ( f06DeckIndex == EMPTY ) break;
      gMeld[COMPUTER][f06MeldPit].Position[f06J] = f06DeckIndex;
    }
    for ( f06K=0; f06K<f06NatInList; f06K++ ) {
      f06DeckIndex = f06NatList[f06K];
      if ( f06DeckIndex == EMPTY ) break;
      gMeld[COMPUTER][f06MeldPit].Position[f06J+f06K] = f06DeckIndex;
    }
    for (f06I=0; f06I<20; f06I++) {
      f06DeckIndex = f06CardList[f06I];
      if ( f06DeckIndex == EMPTY ) break;
      for ( f06J=0; f06J<DECK_SIZE; f06J++ ) {
        f06DeckIndex = gHand[COMPUTER][f06J].Index;
        if ( f06DeckIndex == f06CardList[f06I] ) break;
      }
      gHand[COMPUTER][f06J].Index = EMPTY;
      gHand[COMPUTER][f06J].Rank = '~';
      gHand[COMPUTER][f06J].Selected = false;
      gcHandCardCount--;
    }
    SortHand(COMPUTER);
  }

  return f06Result;
}

/*

This function looks for hex representation in an ascii file. CRLF is
interpreted as the end of line. Each hex digit represents the color
values of 0 through 15. Other values are skipped. The color is then
placed on the screen pixle by pixle. All of the files must be present
for this program to run.

*/

void far GetPixelsFromFile(char *g01FileName, int g01Row, int g01Col,
    bool g01Sideways) {
  int g01Yref = g01Row*gTextHeight;
  int g01Xref = g01Col*gTextWidth;
  int g01X, g01Y, g01Color;
  FILE *g01InFile;
  int g01Width;
  char g01S[640]="";

  g01X=g01Y=g01Color=g01Width=0;
  sprintf(g01S,"%s%s",PATH_TO_CARDS,g01FileName);
  if ( (g01InFile = fopen(g01S, "rb")) == NULL ) {
    sprintf(g01S,"File not found: %s%s",PATH_TO_CARDS,g01FileName);
    Abort(__LINE__,g01S);
    exit( 1 );
  }
  else {

  fgets(g01S, 640, g01InFile );
  while ( !feof(g01InFile) ) {
    g01Width = strlen(g01S);
    for (g01X=0; g01X<g01Width; g01X++) {
      g01Color = EMPTY;
      switch (g01S[g01X]) {
      case '0': g01Color =  0; break;
      case '1': g01Color =  1; break;
      case '2': g01Color =  2; break;
      case '3': g01Color =  3; break;
      case '4': g01Color =  4; break;
      case '5': g01Color =  5; break;
      case '6': g01Color =  6; break;
      case '7': g01Color =  7; break;
      case '8': g01Color =  8; break;
      case '9': g01Color =  9; break;
      case 'A': g01Color = 10; break;
      case 'B': g01Color = 11; break;
      case 'C': g01Color = 12; break;
      case 'D': g01Color = 13; break;
      case 'E': g01Color = 14; break;
      case 'F': g01Color = 15;
      }
      if (g01Sideways) {
        if (g01Color != EMPTY) putpixel( g01Y+312,278-g01X, g01Color );
      }
      else {
        if (g01Color != EMPTY) putpixel( g01X+g01Xref, g01Y+g01Yref, g01Color );
      }
    }
    g01Y++;
    fgets(g01S, 640, g01InFile );
  }
  fclose( g01InFile );

  }
}

/*

This function is intended to be a graphic replacement for a combination
of gotoxy, textcolor, textbachground, and cprintf using va_list,
vsprintf, setcolor, and outtextxy.

*/

void far Gprintf( int g02Row, int g02Col, int g02ForColor, int g02BackColor,
    char *g02FormatString, ... ) {
  va_list g02ArgumentPointer;
  int g02I=0;

  va_start( g02ArgumentPointer, g02FormatString );
  vsprintf( gS, g02FormatString, g02ArgumentPointer );
  char BackStr[2] = {0xDB,0x00};
  setcolor( g02BackColor );
  for (; g02I<strlen( gS ); g02I++)
    outtextxy( (g02Col+g02I) * gTextHeight, g02Row * gTextWidth, BackStr );
  setcolor( g02ForColor );
  outtextxy( g02Col * gTextHeight, g02Row * gTextWidth, gS );
  va_end( g02ArgumentPointer );
}

/*

This function is used to hide the menu after a selection is made.

*/

void far HideMenu(cMenu* h01PullDown, int h01Entries) {
  int h01MenuWidth = strlen(h01PullDown[0].caption);
  int h01Top = h01PullDown[0].row1-1;
  int h01Left = h01PullDown[0].col1-1;
  int h01Bottom = h01PullDown[h01Entries-1].row1+1;
  int h01Right = h01PullDown[h01Entries-1].col1+h01MenuWidth;

  RestoreBehindWindow("MENUBACK.DTA", h01Top, h01Left, h01Bottom+1, h01Right+1);
}

/*

Test for red three and move to Meld0

*/

bool far IsRedThree(int i01Who, int i01N) {
  int i01D;
  bool i01Result = false;

  if (gCard[i01N].Title[0] == '3') {
    switch(gCard[i01N].Suit) {
    case 'H': case 'D': // Red three
      for (i01D=0;i01D<MELD_DEPTH;i01D++) {
        if (gMeld[i01Who][0].Position[i01D] == EMPTY) {
          gMeld[i01Who][0].Position[i01D] = i01N;
          break;
        }
      }
      i01Result = true;
      break;
    }
  }
  return i01Result;
}

/*

Player Meld: Builds a queue of cards from the user selections
displaying a dot for each selection as it goes. It seperates the wilds
from the naturals, allows for only one rank, checks for all wilds and
assigns rank from the user, reverses all selection if failed, includes
the top of the discard pile if for taking, moves cards from the user
hand to his meld pit and returns the rank or blank. Rules for
individual meld are that naturals and wilds add to three cards and that
there are equal or more naturals then wilds in the melded result.

*/

char far pMeld(bool m01ForTake) {
  int m01B,m01C,m01I,m01J,m01N,m01P,m01Q,m01R,m01T,m01W;
  int m01Queue[MELD_DEPTH];
  char m01A,m01RankOfQueue;

  m01B=m01C=m01N=m01P=m01Q=m01R=m01T=m01W=0;
  m01A=m01RankOfQueue=' ';
  for (;m01Q<MELD_DEPTH;m01Q++) m01Queue[m01Q] = EMPTY;
  if (m01ForTake) m01N=1;
  for (m01Q=0;m01Q<MELD_DEPTH;m01Q++) {
    m01A = ReadMenu(gMeldMenu,MELD_PULLDOWN_COUNT);
    if (m01A == 0x0D) break;
    if (m01A == 'x') break;
    m01A = toupper(m01A);
    m01B = SelectCardInHand(PLAYER,m01A);
    if (m01B == EMPTY) m01Q--;
    else {
      for (m01I=1;m01I<=5;m01I++) {
        for (m01J=(22*(m01I-1));m01J<(22*m01I);m01J++) {
          if (m01J>=DECK_SIZE) break;
          if (gHand[PLAYER][m01J].Index != EMPTY) {
            if (gHand[PLAYER][m01J].Selected) {
              Gprintf( STATUS_LINE-(6-m01I), (((22*m01I)-m01J-1)*3)+15, YELLOW,
                BLACK, "%c",0xFE);
            }
          }
        }
      }
      m01C = gHand[PLAYER][m01B].Index;
      m01Queue[m01Q] = m01C;
      if (gCard[m01C].IsWild) {
        m01W++;
      }
      else {
        m01N++;
        if (m01RankOfQueue == ' ') m01RankOfQueue = m01A;
        else {
          if (m01RankOfQueue != m01A) {
            DeselectAllInHand(PLAYER);
            return ' ';
          }
        }
      }
    }
  }
  if (m01RankOfQueue == ' ') {
    if (m01ForTake) return ' ';
    cleardevice();
    Gprintf(1,1,YELLOW,BLACK,
      "On which rank do you want those wilds to be placed?");
    m01A = ReadMenu(gNatualRankMenu,NATURAL_RANK_PULLDOWN_COUNT);
    m01RankOfQueue = toupper(m01A);
  }
  switch (m01RankOfQueue) {
  case '3': m01R= 0; break;
  case '4': m01R= 1; break;
  case '5': m01R= 2; break;
  case '6': m01R= 3; break;
  case '7': m01R= 4; break;
  case '8': m01R= 5; break;
  case '9': m01R= 6; break;
  case 'T': m01R= 7; break;
  case 'J': m01R= 8; break;
  case 'Q': m01R= 9; break;
  case 'K': m01R=10; break;
  case 'A': m01R=11; break;
  default:
    DeselectAllInHand(PLAYER);
    return ' ';
  }
  for(m01T=0;m01T<MELD_DEPTH;m01T++) {
    m01P = gMeld[PLAYER][m01R].Position[m01T];
    if (m01P == EMPTY) break;
    if (gCard[m01P].IsWild)
         m01W++;
    else m01N++;
  }
  if ((m01N+m01W)<3) {
    DeselectAllInHand(PLAYER);
    return ' ';
  }
  else {
    if (m01N<m01W) {
      DeselectAllInHand(PLAYER);
      return ' ';
    }
    else {
      if (m01ForTake) {
        gMeld[PLAYER][m01R].Position[m01T] = gDiscard[gTopPile];
        gDiscard[gTopPile] = EMPTY;
        gTopPile--; m01T++;
      }
      for (m01Q=0;m01Q<MELD_DEPTH;m01Q++,m01T++) {
        if (m01Queue[m01Q] == EMPTY) break;
        gMeld[PLAYER][m01R].Position[m01T] = m01Queue[m01Q];
        for (m01B=0;m01B<DECK_SIZE;m01B++) {
          if (gHand[PLAYER][m01B].Index == m01Queue[m01Q]) break;
        }
        gHand[PLAYER][m01B].Index = EMPTY;
        gHand[PLAYER][m01B].Rank = '~';
        gHand[PLAYER][m01B].Selected = false;
        gpHandCardCount--;
      }
      gpMeldedBefore = true;
      SortHand(PLAYER);
    }
  }
  DeselectAllInHand(PLAYER);

  return m01RankOfQueue;
}

/*

This function melds all the natural cards it can from the computer
hand.

*/

void far cMeldAllNaturals() {
  int  m02CardList[20];
  int  m02I, m02J, m02K;
  int  m02MeldPit;
  int  m02NatCount[11];
  char *m02Ptr;
  char m02RankOfCardInList;
  int  m02DeckIndex;

  for (m02I=0; m02I<11; m02I++) m02NatCount[m02I]= 0;
  for (m02I=0; m02I<DECK_SIZE; m02I++) {
    m02DeckIndex = gHand[COMPUTER][m02I].Index;
    if ( m02DeckIndex == EMPTY ) break;
    m02RankOfCardInList = gCard[m02DeckIndex].Title[0];
    m02Ptr = strchr( gRankString, m02RankOfCardInList );
    switch ( m02RankOfCardInList ) {
    case 'Z':
    case '2':
    case '3':
      break;
    default:
      m02NatCount[(int) (m02Ptr-gRankString)-1]++;
    }
  }
  for (m02I=0; m02I<20; m02I++) m02CardList[m02I] = EMPTY;
  m02RankOfCardInList = ' ';
  for ( m02I=8; m02I>2; m02I--) {
    for ( m02J=10; m02J>=0; m02J-- ) {
      if ( m02NatCount[m02J] == m02I ) {
        m02RankOfCardInList = gRankString[m02J+1];
        m02NatCount[m02J] = 0;
        break;
      }
    }
    if ( m02RankOfCardInList != ' ' ) break;
  }
  if ( m02RankOfCardInList != ' ' ) {
    for (m02I=0, m02J=0; m02I<DECK_SIZE; m02I++) {
      m02DeckIndex = gHand[COMPUTER][m02I].Index;
      if ( m02DeckIndex == EMPTY ) break;
      if ( gCard[m02DeckIndex].Title[0] == m02RankOfCardInList )
        m02CardList[m02J++] = m02DeckIndex;
    }
    m02MeldPit = cFindMeldPit( m02RankOfCardInList );
    if ( m02MeldPit == EMPTY ) {
      switch (m02RankOfCardInList) {
      case '4': m02MeldPit =  1; break;
      case '5': m02MeldPit =  2; break;
      case '6': m02MeldPit =  3; break;
      case '7': m02MeldPit =  4; break;
      case '8': m02MeldPit =  5; break;
      case '9': m02MeldPit =  6; break;
      case 'T': m02MeldPit =  7; break;
      case 'J': m02MeldPit =  8; break;
      case 'Q': m02MeldPit =  9; break;
      case 'K': m02MeldPit = 10; break;
      case 'A': m02MeldPit = 11; break;
      }
    }
    for (m02I=0; m02I<MELD_DEPTH; m02I++) {
      m02DeckIndex = gMeld[COMPUTER][m02MeldPit].Position[m02I];
      if ( m02DeckIndex == EMPTY ) break;
    }
    for ( m02J=0; m02J<MELD_DEPTH; m02J++ ) {
      m02DeckIndex = m02CardList[m02J];
      if ( m02DeckIndex == EMPTY ) break;
      gMeld[COMPUTER][m02MeldPit].Position[m02I+m02J] = m02DeckIndex;
      for ( m02K=0; m02K<DECK_SIZE; m02K++ ) {
        m02DeckIndex = gHand[COMPUTER][m02K].Index;
        if ( m02DeckIndex == m02CardList[m02J] ) break;
      }
      gHand[COMPUTER][m02K].Index = EMPTY;
      gHand[COMPUTER][m02K].Rank = '~';
      gHand[COMPUTER][m02K].Selected = false;
      gcHandCardCount--;
    }
    SortHand(COMPUTER);
  }
}

/*

This function returns the value of the minimum legal first meld score
stepped at 15, 50, 90, and 120 for a score from the previous round of
less than 0, 1500, 3000, and greater than 3000 for the computer hand.

*/

int far cMinLegalMeld() {
  int m03MinMeld = 0;

  if (gRounds <= 1) {
    m03MinMeld = 50;
  }
  else {
    if (gScore[gRounds-2][COMPUTER] >= 3000) {
      m03MinMeld = 120;
    }
    else {
      if (gScore[gRounds-2][COMPUTER] >= 1500) {
        m03MinMeld = 90;
      }
      else {
        if (gScore[gRounds-2][COMPUTER] >= 0) {
          m03MinMeld = 50;
        }
        else {
          m03MinMeld = 15;
        }
      }
    }
  }
  return m03MinMeld;
}

/*

This function returns the value of the minimum legal first meld score
stepped at 15, 50, 90, and 120 for a score from the previous round of
less than 0, 1500, 3000, and greater than 3000 for the use hand.
Includes the top of the discard pile if for take. Returns all cards
back to the hand except red threes on fail.

*/

int far pCalcFirstMeld() {
  int c02Result = 0;

  if (gRounds <= 1) c02Result = 50;
  else {
    if (gScore[gRounds-2][PLAYER] >= 3000) c02Result = 120;
    else {
      if (gScore[gRounds-2][PLAYER] >= 1500) c02Result = 90;
      else {
        if (gScore[gRounds-2][PLAYER] >= 0) c02Result = 50;
        else c02Result = 15;
      }
    }
  }

  return c02Result;
}

bool far pMinLegalMeld(bool m04ForTake) {
  int m04L,m04D,m04C,m04CurMeld,m04MinMeld;

  m04L=m04D=m04C=m04CurMeld=m04MinMeld=0;
  m04MinMeld = pCalcFirstMeld();
  for (m04L=1;m04L<MELD_LOCATIONS;m04L++) {
    for (m04D=0;m04D<=MELD_DEPTH;m04D++) {
      m04C = gMeld[PLAYER][m04L].Position[m04D];
      if (m04C == EMPTY) break;
      m04CurMeld += gCard[m04C].Value;
    }
  }
  if ((m04CurMeld > 0 ) && (m04CurMeld < m04MinMeld)) {
    if (m04ForTake) return false;
    cleardevice();
    Gprintf(1,1,YELLOW,BLACK,
      "All melds are being return to your hand.");
    Gprintf(2,1,YELLOW,BLACK,"Press a key to continue.");
    getch();
    gpMeldedBefore = false;
    for (m04C=0;m04C<DECK_SIZE;m04C++) {
      if (gHand[PLAYER][m04C].Index == EMPTY) break;
    }
    for (m04L=1;m04L<MELD_LOCATIONS;m04L++) {
      gMeld[PLAYER][m04L].IsBook = false;
      gMeld[PLAYER][m04L].HasWild = false;
      for (m04D=0;m04D<=MELD_DEPTH;m04D++) {
        if (gMeld[PLAYER][m04L].Position[m04D] == EMPTY) break;
        gHand[PLAYER][m04C].Index = gMeld[PLAYER][m04L].Position[m04D];
        gHand[PLAYER][m04C].Rank = gCard[gHand[PLAYER][m04C].Index].Rank;
        gMeld[PLAYER][m04L].Position[m04D] = EMPTY;
        gpHandCardCount++;
        m04C++;
      }
    }
    SortHand(PLAYER);
    return false;
  }
  return true;
}

/*

This function provides a variety of cardbacks.

*/

void far NextCardBack() {
  int n01A = gLastCB;

  while (n01A == gLastCB) n01A = rand() % 32;
  gLastCB = n01A;
  switch (n01A) {
  case  0: strcpy(gCardBackFileName, "CB0.PXL");   break;
  case  1: strcpy(gCardBackFileName, "CB1.PXL");   break;
  case  2: strcpy(gCardBackFileName, "CB2.PXL");   break;
  case  3: strcpy(gCardBackFileName, "CB3.PXL");   break;
  case  4: strcpy(gCardBackFileName, "CB4.PXL");   break;
  case  5: strcpy(gCardBackFileName, "CB5.PXL");   break;
  case  6: strcpy(gCardBackFileName, "CB6.PXL");   break;
  case  7: strcpy(gCardBackFileName, "CB7.PXL");   break;
  case  8: strcpy(gCardBackFileName, "CB8.PXL");   break;
  case  9: strcpy(gCardBackFileName, "CB9.PXL");   break;
  case 10: strcpy(gCardBackFileName, "CBA.PXL");   break;
  case 11: strcpy(gCardBackFileName, "CBB.PXL");   break;
  case 12: strcpy(gCardBackFileName, "CBC.PXL");   break;
  case 13: strcpy(gCardBackFileName, "CBD.PXL");   break;
  case 14: strcpy(gCardBackFileName, "CBE.PXL");   break;
  case 15: strcpy(gCardBackFileName, "CBF.PXL");   break;
  case 16: strcpy(gCardBackFileName, "BYC_0.PXL"); break;
  case 17: strcpy(gCardBackFileName, "BYC_1.PXL"); break;
  case 18: strcpy(gCardBackFileName, "BYC_2.PXL"); break;
  case 19: strcpy(gCardBackFileName, "BYC_3.PXL"); break;
  case 20: strcpy(gCardBackFileName, "BYC_4.PXL"); break;
  case 21: strcpy(gCardBackFileName, "BYC_5.PXL"); break;
  case 22: strcpy(gCardBackFileName, "BYC_6.PXL"); break;
  case 23: strcpy(gCardBackFileName, "BYC_7.PXL"); break;
  case 24: strcpy(gCardBackFileName, "BYC_8.PXL"); break;
  case 25: strcpy(gCardBackFileName, "BYC_9.PXL"); break;
  case 26: strcpy(gCardBackFileName, "BYC_A.PXL"); break;
  case 27: strcpy(gCardBackFileName, "BYC_B.PXL"); break;
  case 28: strcpy(gCardBackFileName, "BYC_C.PXL"); break;
  case 29: strcpy(gCardBackFileName, "BYC_D.PXL"); break;
  case 30: strcpy(gCardBackFileName, "BYC_E.PXL"); break;
  case 31: strcpy(gCardBackFileName, "BYC_F.PXL"); break;
  }
}

/*

This function checks for capability of computer hand to "go out".

*/

void far cOutCapabile() {
  int  o01Pos1;
  int  o01Pos2;
  int  o01I, o01J, o01K;
  int  o01Singletons = 0;
  int  o01Doubletons = 0;
  int  o01NatCount[12];
  int  o01MeldPit;
  int  o01WldCount = 0;
  char *o01Ptr;
  char o01Rank, o01OldRank;
  bool o01Pass = true;

// 14Jul2011 Changed condition from < 1 to < NUMBER_CANASTA_OUT
  if ( gcCanastaCount < NUMBER_CANASTA_OUT ) return;
  for (o01I=0; o01I<12; o01I++) o01NatCount[o01I]= 0;
  for (o01I=0; o01I<DECK_SIZE; o01I++) {
    o01Pos1 = gHand[COMPUTER][o01I].Index;
    if ( o01Pos1 == EMPTY ) break;
    o01Rank = gCard[o01Pos1].Title[0];
    o01Ptr = strchr( gRankString, o01Rank );
    switch ( o01Rank ) {
    case '2':
    case 'Z':
      o01WldCount++;
      break;
    default:
      o01NatCount[(int) (o01Ptr-gRankString)]++;
    }
  }
  for (o01I=0; o01I<12; o01I++) {
    switch ( o01NatCount[o01I] ) {
    case 1:
      if ( ++o01Singletons > 1 ) o01Pass = false;
      break;
    case 2:
      if ( ++o01Doubletons > o01WldCount ) o01Pass = false;
    }
    if ( o01Pass == false ) break;
  }
  if ( o01Doubletons != o01WldCount ) o01Pass = false;
  if ( o01Pass ) {
    o01Singletons = 0;
    o01OldRank = ' ';
    for (o01I=0; o01I<DECK_SIZE; o01I++) {
      o01Pos1 = gHand[COMPUTER][o01I].Index;
      if ( o01Pos1 == EMPTY ) break;
      o01Rank = gCard[o01Pos1].Title[0];
      if ( o01OldRank == ' ' ) {
        o01Singletons++;
        o01MeldPit = EMPTY;
        o01MeldPit = cFindMeldPit( o01Rank );
        if ( o01MeldPit == EMPTY ) {
          switch (o01Rank) {
          case '3': o01MeldPit =  0; break;
          case '4': o01MeldPit =  1; break;
          case '5': o01MeldPit =  2; break;
          case '6': o01MeldPit =  3; break;
          case '7': o01MeldPit =  4; break;
          case '8': o01MeldPit =  5; break;
          case '9': o01MeldPit =  6; break;
          case 'T': o01MeldPit =  7; break;
          case 'J': o01MeldPit =  8; break;
          case 'Q': o01MeldPit =  9; break;
          case 'K': o01MeldPit = 10; break;
          case 'A': o01MeldPit = 11; break;
          }
        }
        for ( o01J=0; o01J<MELD_DEPTH; o01I++) {
          o01Pos2 = gMeld[COMPUTER][o01MeldPit].Position[o01J];
          if ( o01Pos2 == EMPTY ) break;
        }
        gMeld[COMPUTER][o01MeldPit].Position[o01J] = o01Pos1;
        gHand[COMPUTER][o01I].Index = EMPTY;
        gHand[COMPUTER][o01I].Rank = '~';
        gHand[COMPUTER][o01I].Selected = false;
        gcHandCardCount--;
      }
      else {
        if ( o01Rank == o01OldRank ) {
          o01Singletons++;
          gMeld[COMPUTER][o01MeldPit].Position[o01J] = o01Pos1;
          gHand[COMPUTER][o01I].Index = EMPTY;
          gHand[COMPUTER][o01I].Rank = '~';
          gHand[COMPUTER][o01I].Selected = false;
          gcHandCardCount--;
        }
        else {
          if ( o01Singletons == 2 ) {
            for ( o01K=0; o01K<DECK_SIZE; o01K++ ) {
              o01Pos2 = gHand[COMPUTER][o01K].Index;
              if ((gCard[o01Pos2].Title[0] == 'Z') ||
                  (gCard[o01Pos2].Title[0] == '2')) {
                gMeld[COMPUTER][o01MeldPit].Position[o01J] = o01Pos2;
                gHand[COMPUTER][o01K].Index = EMPTY;
                gHand[COMPUTER][o01K].Rank = '~';
                gHand[COMPUTER][o01K].Selected = false;
                gcHandCardCount--;
                break;
              }
            }
          }
          o01Singletons = 1;
          o01MeldPit = EMPTY;
          o01MeldPit = cFindMeldPit( o01Rank );
          if ( o01MeldPit == EMPTY ) {
            switch (o01Rank) {
            case '3': o01MeldPit =  0; break;
            case '4': o01MeldPit =  1; break;
            case '5': o01MeldPit =  2; break;
            case '6': o01MeldPit =  3; break;
            case '7': o01MeldPit =  4; break;
            case '8': o01MeldPit =  5; break;
            case '9': o01MeldPit =  6; break;
            case 'T': o01MeldPit =  7; break;
            case 'J': o01MeldPit =  8; break;
            case 'Q': o01MeldPit =  9; break;
            case 'K': o01MeldPit = 10; break;
            case 'A': o01MeldPit = 11; break;
            }
          }
          for ( o01J=0; o01J<MELD_DEPTH; o01I++) {
            o01Pos2 = gMeld[COMPUTER][o01MeldPit].Position[o01J];
            if ( o01Pos2 == EMPTY ) break;
          }
          gMeld[COMPUTER][o01MeldPit].Position[o01J] = o01Pos1;
          gHand[COMPUTER][o01I].Index = EMPTY;
          gHand[COMPUTER][o01I].Rank = '~';
          gHand[COMPUTER][o01I].Selected = false;
          gcHandCardCount--;
        }
      }
      o01OldRank = o01Rank;
    }
    SortHand(COMPUTER);
  }

  return;
}

/*

This function enables the mouse environment while waiting for user
input.

*/

char far ReadDesktop() {
  char r01KeyStroke[3] = "";
  bool r01Continuing=true;
#ifdef USE_MOUSE
  int r01I=0;
  int r01SaveX=gMouseInformation.x;
  int r01SaveY=gMouseInformation.y;

  MouseOn( &gMouseInformation );
#endif
  while ( r01Continuing ) {
    r01KeyStroke[0] = r01KeyStroke[1] = r01KeyStroke[2] = 0x00;
#ifdef USE_MOUSE
    while ( kbhit() ) getch();
    while ( !kbhit()
      && !MouseHit( &gMouseInformation )
      ) {
      if ((r01SaveX!=gMouseInformation.x)||(r01SaveY!=gMouseInformation.y)) {
        Gprintf( STATUS_LINE, 75, STATUS_FOR, STATUS_BACK, "%2d,%2d",
          gMouseInformation.y-1, gMouseInformation.x-1 );
      }
      r01SaveX = gMouseInformation.x;
      r01SaveY = gMouseInformation.y;
    }
#endif
    if ( kbhit() ) {
      r01KeyStroke[0] = getch();
      if ( r01KeyStroke[0] == 0x00 ) {
        r01KeyStroke[1] = getch();
        switch (r01KeyStroke[1]) {
        case 34: r01KeyStroke[0] = 'x'; break;
        case 24: r01KeyStroke[0] = 'y'; break;
        case 35: r01KeyStroke[0] = 'z';
        }
      }
#ifdef USE_MOUSE
      MouseOff( &gMouseInformation ); MouseOn( &gMouseInformation );
#endif
      r01Continuing = false;
    }
#ifdef USE_MOUSE
    if ( MouseHit( &gMouseInformation ) ) {
      MouseGet( &gMouseInformation );
      switch ( gMouseInformation.Button ) {
      case 1:
        for ( r01I=0; r01I<DESKTOP_BUTTON_COUNT; r01I++ ) {
          if (( gMouseInformation.y-1 >= gDesktop[gPhase][r01I].row1 ) &&
              ( gMouseInformation.y-1 <= gDesktop[gPhase][r01I].row2 ) &&
              ( gMouseInformation.x-1 >= gDesktop[gPhase][r01I].col1 ) &&
              ( gMouseInformation.x-1 <= gDesktop[gPhase][r01I].col2 ) ) {
            r01KeyStroke[0] = gDesktop[gPhase][r01I].letter;
            r01Continuing = false;
            break;
          }
        }
        if (r01Continuing) {
          r01KeyStroke[0] = 0x00;
          r01Continuing = false;
        }
        break;
      case 2:
        r01KeyStroke[0] = 0x1B;
        r01Continuing = false;
      }
    }
#endif
    // Otherwize continue
  }
#ifdef USE_MOUSE
  MouseOff( &gMouseInformation );
#endif
  if ( r01KeyStroke[0] ) {
    if ((r01KeyStroke[0] >= 'A') && (r01KeyStroke[0] <= 'Z')) {
      // lowercase
      r01KeyStroke[0] += ' ';
    }
  }

  return r01KeyStroke[0];
}

/*

This largely redundant function repeats the one above, but with respect
to a pull-down menu. The desktop is disabled while in this function.

*/

char far ReadMenu(cMenu *r02PullDown, int r02Entries) {
  char r02KeyStroke[3];
  bool r02Continuing=true;

  ShowMenu(r02PullDown,r02Entries);
#ifdef USE_MOUSE
  int r02I=0;
  MouseOn( &gMouseInformation );
#endif
  while ( r02Continuing ) {
    r02KeyStroke[0] = r02KeyStroke[1] = r02KeyStroke[2] = NULL;
#ifdef USE_MOUSE
    while ( kbhit() ) getch();
    while ( !kbhit() && !MouseHit( &gMouseInformation ) );
#endif
    if ( kbhit() ) {
      r02KeyStroke[0] = getch();
      if ( r02KeyStroke[0] == NULL ) r02KeyStroke[1] = getch();
#ifdef USE_MOUSE
      MouseOff( &gMouseInformation ); MouseOn( &gMouseInformation );
#endif
      r02Continuing = false;
    }
#ifdef USE_MOUSE
    if ( MouseHit( &gMouseInformation ) ) {
      MouseGet( &gMouseInformation );
      switch ( gMouseInformation.Button ) {
      case 1:
        for ( r02I=0; r02I<r02Entries; r02I++ ) {
          if (( gMouseInformation.y-1 >= r02PullDown[r02I].row1 ) &&
              ( gMouseInformation.y-1 <= r02PullDown[r02I].row2 ) &&
              ( gMouseInformation.x-1 >= r02PullDown[r02I].col1 ) &&
              ( gMouseInformation.x-1 <= r02PullDown[r02I].col2 ) ) {
            r02KeyStroke[0] = r02PullDown[r02I].letter;
            r02Continuing = false;
            break;
          }
        }
        if (r02Continuing) {
          r02KeyStroke[0] = 0x00;
          r02Continuing = false;
        }
        break;
      case 2:
        r02KeyStroke[0] = 0x1B;
        r02Continuing = false;
      }
    }
#endif
    // Otherwize continue
  }
#ifdef USE_MOUSE
  MouseOff( &gMouseInformation );
#endif
  if ( r02KeyStroke[0] ) {
    if ((r02KeyStroke[0] >= 'A') && (r02KeyStroke[0] <= 'Z')) {
      // lowercase
      r02KeyStroke[0] += ' ';
    }
  }
  HideMenu(r02PullDown,r02Entries);

  return r02KeyStroke[0];
}

/*

This function refreshes the screen from top to bottom.

*/

void far Refresh() {
  int r03I,r03J,r03A,r03N;

  r03I=r03J=r03A=r03N=0;
  cleardevice();

  /*

  Special case: Search for red threes in both hands to correct for
  taking pile with a red three at bottom from begining of round.

  */
  gcHandCardCount = 0;
  for (r03I=DECK_SIZE-1;r03I>=0;r03I--) {
    r03N = gHand[COMPUTER][r03I].Index;
    if (r03N != EMPTY) {
      gcHandCardCount++;
      if (IsRedThree(COMPUTER,r03N)) {
        gHand[COMPUTER][r03I].Index = EMPTY;
        gHand[COMPUTER][r03I].Rank = '~';
        gHand[COMPUTER][r03I].Selected = false;
        gcHandCardCount--;
        SortHand(COMPUTER);
      }
    }
  }
  gpHandCardCount = 0;
  for (r03I=DECK_SIZE-1;r03I>=0;r03I--) {
    r03N = gHand[PLAYER][r03I].Index;
    if (r03N != EMPTY) {
      gpHandCardCount++;
      if (IsRedThree(PLAYER,r03N)) {
        gHand[PLAYER][r03I].Index = EMPTY;
        gHand[PLAYER][r03I].Rank = '~';
        gHand[PLAYER][r03I].Selected = false;
        gpHandCardCount--;
        SortHand(PLAYER);
      }
    }
  }

  /*

  Computer Hand gHand0 -- only the bottom row card backs in two rows
  for 108 cards

  */

  for (r03I=DECK_SIZE-1;r03I>=54;r03I--) {
    r03N = gHand[COMPUTER][r03I].Index;
    if (r03N != EMPTY) {
      GetPixelsFromFile( gCardBackFileName, -7, (107-r03I)+18, false );
    }
  }
  for (r03I=53;r03I>=0;r03I--) {
    if (gHand[COMPUTER][r03I].Index != EMPTY) {
#ifdef TESTING
// Face up display of hand
      DisplayCard(gHand[COMPUTER][r03I].Index, -8, r03I*2, false);
#else
      GetPixelsFromFile( gCardBackFileName, -9, (53-r03I)+18, false );
#endif
    }
  }

  // Computer Melds -- all threes as Meld0

  ShowMelds(COMPUTER,5);

  // Score Pad -- showing written bonus and melds

  ShowScore();

  // Stock -- with number of cards left

  Gprintf(STOCK_ROW-1,STOCK_COLUMN+3,YELLOW,BLACK,"%3d",
    gNextCardInStock+1);
  if (gNextCardInStock >= 0) {
    GetPixelsFromFile( "DECKSIDE.PXL",    STOCK_ROW, STOCK_COLUMN-1,
      false );
    GetPixelsFromFile( gCardBackFileName, STOCK_ROW, STOCK_COLUMN,
      false );
  }

  // Discard Pile -- with wilds and red threes sideways

  if (gTopPile <= EMPTY) gTopPile = EMPTY; // bug fix
  for (r03I=0;r03I<DECK_SIZE;r03I++) {
    r03A = gDiscard[r03I];
    if (r03A == EMPTY) break;
    else {
      if (gCard[r03A].IsWild) {
        DisplayCard(r03A,STOCK_ROW,STOCK_COLUMN+9,true);
      }
      else {
        if ((gCard[r03A].Title[0] == '3') &&
           ((gCard[r03A].Title[1] == 'H') ||
            (gCard[r03A].Title[1] == 'D'))) {
          DisplayCard(r03A,STOCK_ROW,STOCK_COLUMN+9,true);
        }
        else DisplayCard(r03A,STOCK_ROW,STOCK_COLUMN+9,false);
      }
    }
  }
  Gprintf(STOCK_ROW-1,STOCK_COLUMN+10,YELLOW,BLACK,"%3d",
    gTopPile+1);

  // Player Melds -- all threes as Meld0

  ShowMelds(PLAYER,37);

  /*

  Player Hand -- five rows for 108 cards, last row is hardly ever
  used. The cards have a small designation in the upper right corner.

  */

  for (r03I=1;r03I<=5;r03I++) {
    for (r03J=(22*(r03I-1));r03J<(22*r03I);r03J++) {
      if (r03J>=DECK_SIZE) break;
      if (gHand[PLAYER][r03J].Index != EMPTY) {
        DisplayCard(gHand[PLAYER][r03J].Index, STATUS_LINE-(6-r03I),
          (((22*r03I)-r03J-1)*3)+7, false);
      }
    }
  }

  // Status Line -- showing all currents

  Gprintf(STATUS_LINE, 0,STATUS_FOR,STATUS_BACK, "%80.80s"," " );
  if (gpMeldedBefore) {
    Gprintf(STATUS_LINE, 0,STATUS_FOR,STATUS_BACK,
      " Round %d |", gRounds );
  } else {
    Gprintf(STATUS_LINE, 0,STATUS_FOR,STATUS_BACK,
      " Round %d | first meld = %d |", gRounds, (pCalcFirstMeld()) );
  }
  Gprintf(STATUS_LINE,50,STATUS_FOR,STATUS_BACK, "%s (%s)", PROGNAME,
    VERSION );

  // Desktop Menu Bar

  Gprintf( 0, 0, BLACK, WHITE, "%80.80s"," " );
  for (r03I=0;r03I<DESKTOP_BUTTON_COUNT;r03I++) {
    Gprintf(gDesktop[gPhase][r03I].row1,gDesktop[gPhase][r03I].col1,BLACK,
      WHITE, "%s", gDesktop[gPhase][r03I].caption );
    Gprintf(gDesktop[gPhase][r03I].row1,gDesktop[gPhase][r03I].col1+1,RED,
      WHITE, "%c", gDesktop[gPhase][r03I].caption[1] );
  }

  // Check if Player or Computer is out, or if the Stock is empty.

  if (gpHandCardCount <= 0)      gEndRound = true;
  if (gcHandCardCount <= 0)      gEndRound = true;
  if (gNextCardInStock == EMPTY) gEndRound = true;
}

/*

This function restores pixels behind a pull-down menu from a file.

*/

void far RestoreBehindWindow(char *r04FileName, int r04Top, int r04Left,
       int r04Bottom, int r04Right) {
  int r04I, r04J;
  int r04PixelTop = r04Top*gTextHeight;
  int r04PixelLeft = r04Left*gTextWidth;
  int r04PixelBottom = ((r04Bottom+1)*gTextHeight)-1;
  int r04PixelRight = ((r04Right+1)*gTextWidth)-1;
  FILE *r04InFile;
  char r04InChar = ' ';

  r04I=r04J=0;
  if ( (r04InFile = fopen(r04FileName, "rb")) == NULL ) {
    ProgramDestructor();
    printf("Error in %s: Cannot open %s file.\n", PROGNAME, r04FileName);
    exit( 2 );
  }

  for (r04I=r04PixelTop;r04I<=r04PixelBottom;r04I++) {
    for (r04J=r04PixelLeft;r04J<=r04PixelRight;r04J++) {
      r04InChar = fgetc( r04InFile );
      switch (r04InChar) {
      case '0': putpixel(r04J,r04I, 0); break;
      case '1': putpixel(r04J,r04I, 1); break;
      case '2': putpixel(r04J,r04I, 2); break;
      case '3': putpixel(r04J,r04I, 3); break;
      case '4': putpixel(r04J,r04I, 4); break;
      case '5': putpixel(r04J,r04I, 5); break;
      case '6': putpixel(r04J,r04I, 6); break;
      case '7': putpixel(r04J,r04I, 7); break;
      case '8': putpixel(r04J,r04I, 8); break;
      case '9': putpixel(r04J,r04I, 9); break;
      case 'A': putpixel(r04J,r04I,10); break;
      case 'B': putpixel(r04J,r04I,11); break;
      case 'C': putpixel(r04J,r04I,12); break;
      case 'D': putpixel(r04J,r04I,13); break;
      case 'E': putpixel(r04J,r04I,14); break;
      default : putpixel(r04J,r04I,15);
      }
    }
  }
  fclose(r04InFile);
}

/*

This function restores the state of the computer to file.

*/

void far RestoreStateOfComputer() {
  FILE *r05InFile;
  int r05I,r05J,r05K;

  r05InFile = fopen("SAVESTAT.DTA","rb");

// Card Deck

  for (r05I=0;r05I<DECK_SIZE;r05I++) {
    fgets(gS,80,r05InFile);
    gCard[r05I].Shuffle[0] = gS[0];
    gCard[r05I].Shuffle[1] = gS[1];
    gCard[r05I].Shuffle[2] = gS[2];
    gCard[r05I].Shuffle[3] = gS[3];
    gCard[r05I].Title[0] = gS[4];
    gCard[r05I].Title[1] = gS[5];
    gCard[r05I].Title[2] = gS[6];
    gCard[r05I].Rank = gS[7];
    gCard[r05I].Suit = gS[8];
    gS[0] = gS[9];
    gS[1] = gS[10];
    gS[2] = gS[11];
    gS[3] = 0x00;
    gCard[r05I].Value = atoi(gS);
    if (gS[12] == 'T')
         gCard[r05I].IsWild = true;
    else gCard[r05I].IsWild = false;
  }

// Hands

  gpHandCardCount = 0;
  gcHandCardCount = 0;
  for (r05I=0;r05I<NUM_PLAYERS;r05I++) {
    for (r05J=0;r05J<DECK_SIZE;r05J++) {
      fgets(gS,80,r05InFile);
      gHand[r05I][r05J].Rank = gS[0];
      gS[0] = gS[1];
      gS[1] = gS[2];
      gS[2] = gS[3];
      gS[3] = 0x00;
      gHand[r05I][r05J].Index = atoi(gS);
      if (gS[4] == 'T')
           gHand[r05I][r05J].Selected = true;
      else gHand[r05I][r05J].Selected = false;
      if (r05I == PLAYER) gpHandCardCount++;
      if (r05I == COMPUTER) gcHandCardCount++;
    }
  }

// Top Discard Pile

  fgets(gS,80,r05InFile);
  gS[3] = 0x00;
  gTopPile = atoi(gS);

// Stock

  for (r05I=0;r05I<DECK_SIZE;r05I++) {
    fgets(gS,80,r05InFile);
    gS[3] = 0x00;
    gStock[r05I] = atoi(gS);
  }

// Discard Pile

  for (r05I=0;r05I<DECK_SIZE;r05I++) {
    fgets(gS,80,r05InFile);
    gS[3] = 0x00;
    gDiscard[r05I] = atoi(gS);
  }

// Melds and Red Trey

  for (r05I=0;r05I<NUM_PLAYERS;r05I++) {
    for (r05J=0;r05J<MELD_LOCATIONS;r05J++) {
      fgets(gS,80,r05InFile);
      if (gS[0] == 'T')
           gMeld[r05I][r05J].IsBook = true;
      else gMeld[r05I][r05J].IsBook = false;
      if (gS[1] == 'T')
           gMeld[r05I][r05J].HasWild = true;
      else gMeld[r05I][r05J].HasWild = false;
      for (r05K=0;r05K<MELD_DEPTH;r05K++) {
        gS[0] = gS[(r05K*3)+2];
        gS[1] = gS[(r05K*3)+3];
        gS[2] = gS[(r05K*3)+4];
        gS[3] = 0x00;
        gMeld[r05I][r05J].Position[r05K] = atoi(gS);
      }
    }
  }

// Score

  for (r05I=0;r05I<MAX_ROUNDS;r05I++) {
    fgets(gS,80,r05InFile);
    gS[60] = gS[5];
    gS[61] = gS[6];
    gS[62] = gS[7];
    gS[63] = gS[8];
    gS[64] = gS[9];
    gS[5] = 0x00;
    gBonusPoints[r05I][0] = atoi(gS);
    gS[0] = gS[60];
    gS[1] = gS[61];
    gS[2] = gS[62];
    gS[3] = gS[63];
    gS[4] = gS[64];
    gS[5] = 0x00;
    gBonusPoints[r05I][1] = atoi(gS);
    fgets(gS,80,r05InFile);
    gS[60] = gS[5];
    gS[61] = gS[6];
    gS[62] = gS[7];
    gS[63] = gS[8];
    gS[64] = gS[9];
    gS[5] = 0x00;
    gMeldPoints[r05I][0] = atoi(gS);
    gS[0] = gS[60];
    gS[1] = gS[61];
    gS[2] = gS[62];
    gS[3] = gS[63];
    gS[4] = gS[64];
    gS[5] = 0x00;
    gMeldPoints[r05I][1] = atoi(gS);
    fgets(gS,80,r05InFile);
    gS[60] = gS[5];
    gS[61] = gS[6];
    gS[62] = gS[7];
    gS[63] = gS[8];
    gS[64] = gS[9];
    gS[5] = 0x00;
    gScore[r05I][0] = atoi(gS);
    gS[0] = gS[60];
    gS[1] = gS[61];
    gS[2] = gS[62];
    gS[3] = gS[63];
    gS[4] = gS[64];
    gS[5] = 0x00;
    gScore[r05I][1] = atoi(gS);
  }

// Miscellaneous

  fgets(gS,80,r05InFile);
  if (gS[0] == 'T')
       gcMeldedBefore = true;
  else gcMeldedBefore = false;
  if (gS[1] == 'T')
       gpMeldedBefore = true;
  else gpMeldedBefore = false;
  gS[0] = gS[2];
  gS[1] = gS[3];
  gS[2] = gS[4];
  gS[3] = 0x00;
  gNextCardInStock = atoi(gS);
  gS[0] = gS[5];
  gS[1] = gS[6];
  gS[2] = gS[7];
  gS[3] = 0x00;
  gRounds = atoi(gS);
  fclose(r05InFile);
  Refresh();
}

/*

This function saves the state of the computer to file.

*/

void far SaveStateOfComputer() {
  FILE *s02OutFile;
  int s02I,s02J,s02K;

  s02OutFile = fopen("SAVESTAT.DTA","wb");

// Card Deck

  for (s02I=0;s02I<DECK_SIZE;s02I++) {
    fprintf(s02OutFile,"%c",gCard[s02I].Shuffle[0]);
    fprintf(s02OutFile,"%c",gCard[s02I].Shuffle[1]);
    fprintf(s02OutFile,"%c",gCard[s02I].Shuffle[2]);
    fprintf(s02OutFile,"%c",gCard[s02I].Shuffle[3]);
    fprintf(s02OutFile,"%c",gCard[s02I].Title[0]);
    fprintf(s02OutFile,"%c",gCard[s02I].Title[1]);
    fprintf(s02OutFile,"%c",gCard[s02I].Title[2]);
    fprintf(s02OutFile,"%c",gCard[s02I].Rank);
    fprintf(s02OutFile,"%c",gCard[s02I].Suit);
    fprintf(s02OutFile,"%3.1d",gCard[s02I].Value);
    if (gCard[s02I].IsWild)
         fprintf(s02OutFile,"T\r\n");
    else fprintf(s02OutFile,"F\r\n");
  }

// Hands

  for (s02I=0;s02I<NUM_PLAYERS;s02I++) {
    for (s02J=0;s02J<DECK_SIZE;s02J++) {
      fprintf(s02OutFile,"%c",gHand[s02I][s02J].Rank);
      fprintf(s02OutFile,"%3.1d",gHand[s02I][s02J].Index);
      if (gHand[s02I][s02J].Selected)
           fprintf(s02OutFile,"T\r\n");
      else fprintf(s02OutFile,"F\r\n");
    }
  }

// Top Discard Pile

  fprintf(s02OutFile,"%3.1d\r\n",gTopPile);

// Stock

  for (s02I=0;s02I<DECK_SIZE;s02I++)
    fprintf(s02OutFile,"%3.1d\r\n",gStock[s02I]);

// Discard Pile

  for (s02I=0;s02I<DECK_SIZE;s02I++)
    fprintf(s02OutFile,"%3.1d\r\n",gDiscard[s02I]);

// Melds and Red Trey

  for (s02I=0;s02I<NUM_PLAYERS;s02I++) {
    for (s02J=0;s02J<MELD_LOCATIONS;s02J++) {
      if (gMeld[s02I][s02J].IsBook)
           fprintf(s02OutFile,"T");
      else fprintf(s02OutFile,"F");
      if (gMeld[s02I][s02J].HasWild)
           fprintf(s02OutFile,"T");
      else fprintf(s02OutFile,"F");
      for (s02K=0;s02K<MELD_DEPTH;s02K++)
        fprintf(s02OutFile,"%3.1d",gMeld[s02I][s02J].Position[s02K]);
      fprintf(s02OutFile,"\r\n");
    }
  }

// Score

  for (s02I=0;s02I<MAX_ROUNDS;s02I++) {
    for (s02J=0;s02J<NUM_PLAYERS;s02J++) {
      fprintf(s02OutFile,"%5.1d",gBonusPoints[s02I][s02J]);
    }
    fprintf(s02OutFile,"\r\n");
    for (s02J=0;s02J<NUM_PLAYERS;s02J++) {
      fprintf(s02OutFile,"%5.1d",gMeldPoints[s02I][s02J]);
    }
    fprintf(s02OutFile,"\r\n");
    for (s02J=0;s02J<NUM_PLAYERS;s02J++) {
      fprintf(s02OutFile,"%5.1d",gScore[s02I][s02J]);
    }
    fprintf(s02OutFile,"\r\n");
  }

// Miscellaneous

  if (gcMeldedBefore)
       fprintf(s02OutFile,"T");
  else fprintf(s02OutFile,"F");
  if (gpMeldedBefore)
       fprintf(s02OutFile,"T");
  else fprintf(s02OutFile,"F");
  fprintf(s02OutFile,"%3.1d",gNextCardInStock);
  fprintf(s02OutFile,"%3.1d\r\n",gRounds);
  fclose(s02OutFile);
}

/*

This function saves pixels behind a pull-down menu into a file.

*/

void far SaveBehindWindow(char *s01FileName, int s01Top, int s01Left,
          int s01Bottom, int s01Right) {
  int s01I, s01J, s01ColorBuffer;
  int s01PixelTop = s01Top*gTextHeight;
  int s01PixelLeft = s01Left*gTextWidth;
  int s01PixelBottom = ((s01Bottom+1)*gTextHeight)-1;
  int s01PixelRight = ((s01Right+1)*gTextWidth)-1;
  FILE *s01OutFile;
  char s01OutChar=' ';

  s01I=s01J=s01ColorBuffer=0;
  s01OutFile = fopen(s01FileName, "wb");
  for (s01I=s01PixelTop;s01I<=s01PixelBottom;s01I++) {
    for (s01J=s01PixelLeft;s01J<=s01PixelRight;s01J++) {
      s01ColorBuffer = getpixel(s01J,s01I);
      switch (s01ColorBuffer) {
      case  0: s01OutChar = '0'; break;
      case  1: s01OutChar = '1'; break;
      case  2: s01OutChar = '2'; break;
      case  3: s01OutChar = '3'; break;
      case  4: s01OutChar = '4'; break;
      case  5: s01OutChar = '5'; break;
      case  6: s01OutChar = '6'; break;
      case  7: s01OutChar = '7'; break;
      case  8: s01OutChar = '8'; break;
      case  9: s01OutChar = '9'; break;
      case 10: s01OutChar = 'A'; break;
      case 11: s01OutChar = 'B'; break;
      case 12: s01OutChar = 'C'; break;
      case 13: s01OutChar = 'D'; break;
      case 14: s01OutChar = 'E'; break;
      default: s01OutChar = 'F';
      }
      fputc( s01OutChar, s01OutFile );
    }
  }
  fclose(s01OutFile);
}

/*

This function returns EMPTY or index in hand for selected occurance.

*/

int far SelectCardInHand(int s03Who, char s03A) {
  int s03I,s03B;

  s03I=s03B=0;
  for (;s03I<DECK_SIZE;s03I++) {
    s03B = gHand[s03Who][s03I].Index;
    if (s03B != EMPTY) {
      if (gCard[s03B].Title[0] == s03A) {
        if (!(gHand[s03Who][s03I].Selected)) {
          gHand[s03Who][s03I].Selected = true;
          return s03I;
        }
      }
    }
  }

  return EMPTY;
}

/*

This function involves the complicated procedure of displaying the
melds of a given side.

*/

void far ShowMelds(int s04Who, int s04Row) {
  int s04I,s04J,s04A;

  s04I=s04J=s04A=0;
  if (s04Who == COMPUTER) gcCanastaCount = 0;
  if (s04Who == PLAYER) gpCanastaCount = 0;
  for (s04I=0;s04I<MELD_LOCATIONS;s04I++) {
    gMeld[s04Who][s04I].IsBook = false;
    gMeld[s04Who][s04I].HasWild = false;
    for (s04J=0;s04J<MELD_DEPTH;s04J++) {
      s04A = gMeld[s04Who][s04I].Position[s04J];
      if (s04A == EMPTY) break;
      if (gCard[s04A].IsWild) gMeld[s04Who][s04I].HasWild = true;
    }
    if (s04J>=7) gMeld[s04Who][s04I].IsBook = true;
  }
  for (s04I=MELD_LOCATIONS-1;s04I>=1;s04I--) {
    if (gMeld[s04Who][s04I].IsBook) {
      if (gMeld[s04Who][s04I].HasWild) {

// Black canasta

        for (s04J=0;s04J<MELD_DEPTH;s04J++) {
          s04A = gMeld[s04Who][s04I].Position[s04J];
          if (gCard[s04A].IsWild) {
            DisplayCard(s04A,s04Row+4,s04I*6, false);
            break;
          }
        }
        for (s04J=0;s04J<MELD_DEPTH;s04J++) {
          s04A = gMeld[s04Who][s04I].Position[s04J];
          if (!(gCard[s04A].IsWild)) {
            DisplayCard(s04A,s04Row+5,s04I*6, false);
            break;
          }
        }
      }
      else {

// Red canasta

        for (s04J=0;s04J<MELD_DEPTH;s04J++) {
          s04A = gMeld[s04Who][s04I].Position[s04J];
          if (!(gCard[s04A].IsWild)) {
            if ((gCard[s04A].Suit == 'H') || (gCard[s04A].Suit == 'D')) {
              DisplayCard(s04A,s04Row+5,s04I*6, false);
              break;
            }
          }
        }
      }
      GetPixelsFromFile("DECKSIDE.PXL",s04Row+5,(s04I*6)-1, false );
      if (s04Who == COMPUTER) gcCanastaCount++;
      if (s04Who == PLAYER) gpCanastaCount++;
    }
    else {

// Non-canasta

      for (s04J=0;s04J<6;s04J++) {
        if (gMeld[s04Who][s04I].Position[s04J] == EMPTY) break;
        DisplayCard(gMeld[s04Who][s04I].Position[s04J], s04J+s04Row, s04I*6, false );
      }
    }
  }
  for (s04J=0;s04J<8;s04J++) {

// Threes

    if (gMeld[s04Who][0].Position[s04J] != EMPTY) {
      DisplayCard(gMeld[s04Who][0].Position[s04J], s04J+s04Row, 0, false );
    }
  }
}

/*

This function displays a specified menu with specified number of
entries.

*/

void far ShowMenu(cMenu *s05PullDown, int s05Entries) {
  int s05I=0;
  int s05MenuWidth = strlen(s05PullDown[0].caption);
  int s05Top = s05PullDown[0].row1-1;
  int s05Left = s05PullDown[0].col1-1;
  int s05Bottom  = s05PullDown[s05Entries-1].row1+1;
  int s05Right  = s05PullDown[s05Entries-1].col1+s05MenuWidth;

  SaveBehindWindow("MENUBACK.DTA", s05Top, s05Left, s05Bottom +1, s05Right +1);
  Gprintf(s05Top, s05Left, BLACK, WHITE, "Ú");
  for (s05I=0;s05I<s05MenuWidth;s05I++ )
    Gprintf(s05Top, s05PullDown[0].col1+s05I, BLACK, WHITE, "Ä");
  Gprintf(s05Top, s05PullDown[0].col1+s05MenuWidth, BLACK, WHITE, "¿");
  for (s05I=0;s05I<s05Entries;s05I++) {
    Gprintf(s05PullDown[s05I].row1, s05PullDown[s05I].col1-1, BLACK, WHITE, "³");
    Gprintf(s05PullDown[s05I].row1, s05PullDown[s05I].col1, BLACK, WHITE,
      "%*.*s", s05MenuWidth, s05MenuWidth, s05PullDown[s05I].caption);
    Gprintf(s05PullDown[s05I].row1, s05PullDown[s05I].col1+s05MenuWidth,
      BLACK, WHITE, "³%c",0xB2);
    Gprintf(s05PullDown[s05I].row1, s05PullDown[s05I].col1+1,
      RED, WHITE, "%c", s05PullDown[s05I].caption[1]);
  }
  Gprintf(s05Bottom , s05Left, BLACK, WHITE, "À");
  for (s05I=1;s05I<=s05MenuWidth;s05I++ )
    Gprintf(s05Bottom , s05Left+s05I, BLACK, WHITE, "Ä");
  Gprintf(s05Bottom , s05Right, BLACK, WHITE, "Ù%c",0xB2);
  for (s05I=1;s05I<=s05MenuWidth+2;s05I++ )
    Gprintf(s05Bottom +1, s05Left+s05I, BLACK, WHITE, "%c",0xB2);
}

/*

This function displays the running table of scores.

*/

void far ShowScore() {
  int s06I;

  if (gRounds<=1) return;
  Gprintf(STOCK_ROW-1, 1,YELLOW,BLACK,"    Player | Computer");
  for (s06I=1;s06I<gRounds;s06I++) {
    if (gScore[s06I-1][PLAYER] == 0) break;
    Gprintf(STOCK_ROW+(s06I*4)-4, 1,YELLOW,BLACK,"B:");
    Gprintf(STOCK_ROW+(s06I*4)-4, 3,YELLOW,BLACK,"%9.1d",
      gBonusPoints[s06I-1][PLAYER]);
    Gprintf(STOCK_ROW+(s06I*4)-4,12,YELLOW,BLACK,"|%9.1d",
      gBonusPoints[s06I-1][COMPUTER]);
    Gprintf(STOCK_ROW+(s06I*4)-3, 1,YELLOW,BLACK,"M:");
    Gprintf(STOCK_ROW+(s06I*4)-3, 3,YELLOW,BLACK,"%9.1d",
      gMeldPoints[s06I-1][PLAYER]);
    Gprintf(STOCK_ROW+(s06I*4)-3,12,YELLOW,BLACK,"|%9.1d",
      gMeldPoints[s06I-1][COMPUTER]);
    Gprintf(STOCK_ROW+(s06I*4)-2, 1,YELLOW,BLACK,"  ---------|---------");
    Gprintf(STOCK_ROW+(s06I*4)-1, 1,YELLOW,BLACK,"T:");
    Gprintf(STOCK_ROW+(s06I*4)-1, 3,YELLOW,BLACK,"%9.1d",
      gScore[s06I-1][PLAYER]);
    Gprintf(STOCK_ROW+(s06I*4)-1,12,YELLOW,BLACK,"|%9.1d",
      gScore[s06I-1][COMPUTER]);
  }
}

/*

This function shuffles the deck.

*/

void far ShuffleDeck() {
  int s07I;

  for (s07I=0;s07I<DECK_SIZE;s07I++) {
    sprintf(gRecord[s07I]  ,"%3.3s",gCard[s07I].Shuffle);
    sprintf(gRecord[s07I]+3,"%2.2s",gCard[s07I].Title);
    sprintf(gRecord[s07I]+5,"%c",gCard[s07I].Rank);
    sprintf(gRecord[s07I]+6,"%c",gCard[s07I].Suit);
    sprintf(gRecord[s07I]+7,"%2d",gCard[s07I].Value);
    if (gCard[s07I].IsWild)
         sprintf(gRecord[s07I]+9,"T");
    else sprintf(gRecord[s07I]+9,"F");
    gRecord[s07I][10] = 0x00;
  }

  qsort((void *)gRecord, DECK_SIZE, sizeof(gRecord[0]), sort_function);

  for (s07I=0;s07I<DECK_SIZE;s07I++) {
    gCard[s07I].Shuffle[0] = gRecord[s07I][0];
    gCard[s07I].Shuffle[1] = gRecord[s07I][1];
    gCard[s07I].Shuffle[2] = gRecord[s07I][2];
    gCard[s07I].Title[0] = gRecord[s07I][3];
    gCard[s07I].Title[1] = gRecord[s07I][4];
    gCard[s07I].Rank = gRecord[s07I][5];
    gCard[s07I].Suit = gRecord[s07I][6];
    if (gRecord[s07I][9] == 'T')
         gCard[s07I].IsWild = true;
    else gCard[s07I].IsWild = false;
    if (gRecord[s07I][7] == ' ') gS[0] = '0'; else gS[0] = gRecord[s07I][7];
    if (gRecord[s07I][8] == ' ') gS[1] = '0'; else gS[1] = gRecord[s07I][8];
    gS[2] = 0x00;
    gCard[s07I].Value = atoi(gS);
  }
}

/*

This function sorts the specified hand.

*/

void far SortHand(int s08Who) {
  int s08I;

  for (s08I=0;s08I<DECK_SIZE;s08I++) {
    sprintf(gRecord[s08I],"%c",gHand[s08Who][s08I].Rank);
    if (gHand[s08Who][s08I].Index == EMPTY)
         sprintf(gRecord[s08I]+1,"999");
    else sprintf(gRecord[s08I]+1,"%3d",gHand[s08Who][s08I].Index);
    if (gHand[s08Who][s08I].Selected)
         sprintf(gRecord[s08I]+4,"T");
    else sprintf(gRecord[s08I]+4,"F");
    gRecord[s08I][5] = 0x00;
  }

  qsort((void *)gRecord, DECK_SIZE, sizeof(gRecord[0]), sort_function);

  for (s08I=0;s08I<DECK_SIZE;s08I++) {
    gHand[s08Who][s08I].Rank = gRecord[s08I][0];
    if (gRecord[s08I][4] == 'T')
         gHand[s08Who][s08I].Selected = true;
    else gHand[s08Who][s08I].Selected = false;
    if (gRecord[s08I][1] == ' ') gS[0] = '0'; else gS[0] = gRecord[s08I][1];
    if (gRecord[s08I][2] == ' ') gS[1] = '0'; else gS[1] = gRecord[s08I][2];
    if (gRecord[s08I][3] == ' ') gS[2] = '0'; else gS[2] = gRecord[s08I][3];
    gS[3] = 0x00;
    gHand[s08Who][s08I].Index = atoi(gS);
    if (gHand[s08Who][s08I].Index == 999) gHand[s08Who][s08I].Index = EMPTY;
  }
}

/*

This function starts a new round.

*/

void far StartOver() {
  int s09I,s09J,s09K;

  s09I=s09J=s09K=0;

  // Reset global variables

  NextCardBack();
  gNextCardInStock = DECK_SIZE-1;
  gTopPile = s09K = EMPTY;
  gEndRound = false;
  gChanged = true;
  gPhase = 0;
// 08Nov2010 Next two lines added
  gpMeldedBefore = false;
  gcMeldedBefore = false;

  // Create Card Deck.

  for (s09I=0; s09I<DECK_SIZE-4; s09I++ ) {
    s09J = s09I%13;
    itoa(rand() % RAND_MAX,gCard[s09I].Shuffle,36);
    gCard[s09I].Title[0] = gRankString[s09J];
    gCard[s09I].Rank = 'a'+(13-s09J);
    if (s09J == 0) {
      s09K++;
      s09K %= 4;
    }
    gCard[s09I].Title[1] = gSuitString[s09K];
    gCard[s09I].Title[2] = 0x00;
    gCard[s09I].Suit = gSuitString[s09K];
    switch (gCard[s09I].Title[0]) {
    case '3': case '4': case '5': case '6': case '7':
      gCard[s09I].Value = 5;
      gCard[s09I].IsWild = false;
      break;
    case '8': case '9': case 'T': case 'J': case 'Q': case 'K':
      gCard[s09I].Value = 10;
      gCard[s09I].IsWild = false;
      break;
    case 'A':
      gCard[s09I].Value = 20;
      gCard[s09I].IsWild = false;
      break;
    case '2':
      gCard[s09I].Value = 20;
      gCard[s09I].IsWild = true;
      break;
    }
  }

  // Add jokers

  for (; s09I<DECK_SIZE; s09I++ ) {
    itoa(rand() % RAND_MAX,gCard[s09I].Shuffle,36);
    gCard[s09I].Title[0] = 'Z';
    if ((s09I%2) == 0)
      gCard[s09I].Title[1] = '1';
    else
      gCard[s09I].Title[1] = '2';
    gCard[s09I].Title[2] = 0x00;
    gCard[s09I].Rank = 'a';
    gCard[s09I].Suit = '*';
    gCard[s09I].Value = 50;
    gCard[s09I].IsWild = true;
  }

  ShuffleDeck();

  // Clear the Table.

  for (s09I=0;s09I<NUM_PLAYERS;s09I++) {
    for (s09J=0;s09J<MELD_LOCATIONS;s09J++) {
      gMeld[s09I][s09J].IsBook = false;
      gMeld[s09I][s09J].HasWild = false;
      for (s09K=0;s09K<MELD_DEPTH;s09K++) {
        gMeld[s09I][s09J].Position[s09K] = EMPTY;
      }
    }
  }
  for (s09I=0;s09I<DECK_SIZE;s09I++) {
    gStock[s09I] = s09I;
    gDiscard[s09I] = EMPTY;
    gHand[COMPUTER][s09I].Index = EMPTY;
    gHand[COMPUTER][s09I].Rank = '~';
    gHand[COMPUTER][s09I].Selected = false;
    gHand[PLAYER][s09I].Index = EMPTY;
    gHand[PLAYER][s09I].Rank = '~';
    gHand[PLAYER][s09I].Selected = false;
  }

  // Deal

  gpHandCardCount = 0;
  gcHandCardCount = 0;
  for (s09I=0;s09I<15;s09I++) {
    for (s09J=0;s09J<NUM_PLAYERS;s09J++) {
      gHand[s09J][s09I].Index = DrawCard(s09J);
      gHand[s09J][s09I].Rank = gCard[gHand[s09J][s09I].Index].Rank;
      if (s09J == PLAYER)   gpHandCardCount++;
      if (s09J == COMPUTER) gcHandCardCount++;
    }
  }
  SortHand(COMPUTER);
  SortHand(PLAYER);

  // Turn up first upcard from stock

  gTopPile++;
  gDiscard[gTopPile] = gStock[gNextCardInStock];
  gStock[gNextCardInStock] = EMPTY;
  gNextCardInStock--;
}

/*

This function checks for wild or three on discard pile, asks user
for a meld, checks meld, sorts hand, moves all discard pile to hand,
erases discard pile, and forces a "draw card" if illegal meld.

*/

bool far pTake() {
  int t01I,t01D;
  char t01A,t01B;

  t01I=t01D=0;
  t01A=t01B=' ';
  if (!(gpMeldedBefore)) return false;
  if (gTopPile == EMPTY) return false;
  t01B = gCard[gDiscard[gTopPile]].Title[0];

  switch (t01B) {
  case 'Z':
  case '2':
  case '3':
    return false;
  }
  t01A = pMeld(true);
  if (t01A == ' ') return false;
  if (!(pMinLegalMeld(true))) return false;
  if (t01A == t01B) {
    for (t01I=0;t01I<DECK_SIZE;t01I++) {
      if (gHand[PLAYER][t01I].Index == EMPTY) {
        break;
      }
    }
    for (;;) {
      t01D = gDiscard[gTopPile];
      gDiscard[gTopPile] = EMPTY;
      gTopPile--;
      gHand[PLAYER][t01I].Index = t01D;
      gHand[PLAYER][t01I].Rank = gCard[t01D].Rank;
      gHand[PLAYER][t01I].Selected = false;
      gpHandCardCount++;
      if (gTopPile == EMPTY) break;
      t01I++;
    }
    SortHand(PLAYER);
  }
  else {
    pDraw();
    return true;
  }
  return true;
}

/*

This function tries to take the discard pile using the computer hand.

*/

bool far cTryTakeDiscard() {
  int t02CardList[20];
  int t02I, t02J, t02K;
  int t02MeldPit;
  int t02NatList[8];
  char t02NatToMeld = gCard[gDiscard[gTopPile]].Title[0];
  int t02NatInHand = 0;
  char t02RankOfCardInList;
  int t02Score = gCard[gDiscard[gTopPile]].Value;
  int t02WildList[12];
  int t02WldInHand = 0;
  int t02DeckIndex;

  if (gTopPile == EMPTY) return false;
  switch ( t02NatToMeld ) {
  case 'Z':
  case '2':
  case '3':
    return false;
  }
  for (t02I=0; t02I<DECK_SIZE; t02I++) {
    t02DeckIndex = gHand[COMPUTER][t02I].Index;
    if ( t02DeckIndex == EMPTY ) return false;
    t02RankOfCardInList = gCard[t02DeckIndex].Title[0];
    if ( t02RankOfCardInList == t02NatToMeld ) break;
  }
  for (t02I=0; t02I<MELD_DEPTH; t02I++) t02CardList[t02I] = EMPTY;
  for (t02I=0; t02I<8; t02I++) t02NatList[t02I] = EMPTY;
  for (t02I=0; t02I<12; t02I++) t02WildList[t02I] = EMPTY;
  t02NatList[0] = gDiscard[gTopPile];
  t02MeldPit = cFindMeldPit( t02NatToMeld );
  for (t02I=0; t02I<DECK_SIZE; t02I++) {
    t02DeckIndex = gHand[COMPUTER][t02I].Index;
    if ( t02DeckIndex == EMPTY ) break;
    t02RankOfCardInList = gCard[t02DeckIndex].Title[0];
    switch ( t02RankOfCardInList ) {
    case 'Z':
    case '2':
      t02WildList[t02WldInHand++] = t02DeckIndex;
    }
    if ( t02RankOfCardInList == t02NatToMeld )
      t02NatList[++t02NatInHand] = t02DeckIndex;
  }
  if ( gWildInDiscardPile ) {
    if ( t02MeldPit == EMPTY ) {
      if ( t02NatInHand < 2 ) return false;
    }
  }
  else {
    if ( t02MeldPit == EMPTY ) {
      if ( t02WldInHand >= 1 ) {
        t02WldInHand = 1;
        t02NatInHand = 1;
      }
      else {
        if ( t02NatInHand < 2 )  return false;
        else {
          t02NatInHand = 2;
        }
      }
    }
  }
  for (t02I=0; t02I<t02NatInHand; t02I++) {
    t02DeckIndex = t02NatList[t02I+1];
    if ( t02DeckIndex == EMPTY ) break;
    t02CardList[t02I] = t02DeckIndex;
    t02Score += gCard[t02DeckIndex].Value;
  }
  for ( t02J=0; t02J<t02WldInHand; t02J++ ) {
    t02DeckIndex = t02WildList[t02J];
    if ( t02DeckIndex == EMPTY ) break;
    t02CardList[t02I + t02J] = t02DeckIndex;
    t02Score += gCard[t02DeckIndex].Value;
  }
  if ( !gcMeldedBefore ) {
    if ( t02Score >= cMinLegalMeld() ) {
      if (( t02NatInHand + t02WldInHand ) >= 2 )
        gcMeldedBefore = true;
      else return false;
    }
    else return false;
  }
  if ( t02MeldPit == EMPTY ) {
    switch (t02NatToMeld) {
    case '3': t02MeldPit= 0; break;
    case '4': t02MeldPit= 1; break;
    case '5': t02MeldPit= 2; break;
    case '6': t02MeldPit= 3; break;
    case '7': t02MeldPit= 4; break;
    case '8': t02MeldPit= 5; break;
    case '9': t02MeldPit= 6; break;
    case 'T': t02MeldPit= 7; break;
    case 'J': t02MeldPit= 8; break;
    case 'Q': t02MeldPit= 9; break;
    case 'K': t02MeldPit=10; break;
    case 'A': t02MeldPit=11; break;
    }
  }
  for (t02I=0; t02I<MELD_DEPTH; t02I++) {
    t02DeckIndex = gMeld[COMPUTER][t02MeldPit].Position[t02I];
    if ( t02DeckIndex == EMPTY ) break;
  }
  for ( t02J=0; t02J<t02WldInHand; t02J++ ) {
    t02DeckIndex = t02WildList[t02J];
    if ( t02DeckIndex == EMPTY ) break;
    gMeld[COMPUTER][t02MeldPit].Position[t02I+t02J] = t02DeckIndex;
    gMeld[COMPUTER][t02MeldPit].HasWild = true;
  }
  for ( t02K=0; t02K<=t02NatInHand; t02K++ ) {
    t02DeckIndex = t02NatList[t02K];
    if ( t02DeckIndex == EMPTY ) break;
    gMeld[COMPUTER][t02MeldPit].Position[t02I+t02J+t02K] = t02DeckIndex;
  }
  for (t02I=0; t02I<20; t02I++) {
    if ( t02CardList[t02I] == EMPTY ) break;
    for ( t02J=0; t02J<DECK_SIZE; t02J++ ) {
      t02DeckIndex = gHand[COMPUTER][t02J].Index;
      if ( t02DeckIndex == t02CardList[t02I] ) break;
    }
    gHand[COMPUTER][t02J].Index = EMPTY;
    gHand[COMPUTER][t02J].Rank = '~';
    gHand[COMPUTER][t02J].Selected = false;
    gcHandCardCount--;
  }
  gDiscard[gTopPile] = EMPTY;
  gTopPile--;
  for (t02I=0; t02I<DECK_SIZE; t02I++) {
    t02DeckIndex = gHand[COMPUTER][t02I].Index;
    if ( t02DeckIndex == EMPTY ) break;
  }
  for ( t02J=0; t02J<=DECK_SIZE; t02J++ ) {
    t02DeckIndex = gDiscard[t02J];
    if ( t02DeckIndex == EMPTY ) break;
    gHand[COMPUTER][t02I+t02J].Index = t02DeckIndex;
    gHand[COMPUTER][t02I+t02J].Rank = gCard[t02DeckIndex].Rank;
    gHand[COMPUTER][t02I+t02J].Selected = false;
    gcHandCardCount++;
    gDiscard[t02J] = EMPTY;
  }
  gTopPile = EMPTY;
  gWildInDiscardPile = false;
  SortHand(COMPUTER);

  return true;
}

/*

This function is used to wait exactly the seconds specified.

*/

void far WaitASec() {
  time_t w01T, w01Tsave;

  w01T = time( NULL );
  w01Tsave = w01T + 1.75;
  while ( w01Tsave > w01T ) w01T = time( NULL );
}

/*

This function returns where a card is located in the computer hand.

*/

int far cWhereInHand( int w02Object ) {
  int w02I;
  int w02Result = EMPTY;
  int w02DeckIndex;

  for (w02I=0;w02I<DECK_SIZE;w02I++) {
    w02DeckIndex = gHand[COMPUTER][w02I].Index;
    if (w02DeckIndex == EMPTY) break;
    if (w02DeckIndex == w02Object) {
      w02Result = w02I;
      break;
    }
  }

  return w02Result;
}

/* ***************************************************************** */

/*

This function constructs the time zone, the graphic environment, random
number sequencing, the mouse environment, and the scorepad.

*/

void far ProgramConstructor() {
  int p01I,p01J,p01GraphError;
  int p01GraphDevice = VGA;
  int p01GraphMode = VGAHI;

  p01I=p01J=p01GraphError=0;
  putenv("TZ=PST8PDT");
  tzset();

  initgraph( &p01GraphDevice, &p01GraphMode, PATH_TO_BGI );
  p01GraphError = graphresult();
  if( p01GraphError != grOk ){
    pd2();
    printf("Path to BGI files: \"%s\".\n", PATH_TO_BGI );
    printf("Graphics error in %s:\n", PROGNAME);
    printf("%s\nPress a key to continue...\n",
      grapherrormsg( p01GraphError ) );
    getch();
    exit( 5 );
  }
  settextstyle(DEFAULT_FONT, HORIZ_DIR, 1);
  gTextHeight = textheight( "H" );
  gTextWidth = textwidth( "M" );

  srand((unsigned) time(NULL));

#ifdef USE_MOUSE
  MouseInit( &gMouseInformation );
  if ( !gMouseInformation.Exist ) {
    ProgramDestructor();
    printf("Error in %s: The mouse does not exist.\n", PROGNAME);
    printf("The mouse is needed for this program.\n");
    printf("Press a key to continue...\n");
    getch();
    exit( 6 );
  }
#endif
  for (p01I=0;p01I<MAX_ROUNDS;p01I++) {
    for (p01J=0;p01J<NUM_PLAYERS;p01J++) {
      gBonusPoints[p01I][p01J] = 0;
      gMeldPoints[p01I][p01J]  = 0;
      gScore[p01I][p01J]       = 0;
    }
  }
  StartOver();
}

/*

This function is the main loop. It refreshes the graphic screen
if changed, processes the end of round and the end of game, reads
the desktop menu from the user, and processes the desktop menu
options.

*/

bool far MainLoop() {
  char m05Answer[3] = "  ";

  if (gChanged) Refresh();
  gChanged = false;
  if (gEndRound) {
    FigureScore(gRounds-1);
    Gprintf( 0, 1, BLACK, WHITE, " End of Round               ");
    Gprintf( 1, 1, BLACK, WHITE, " Press a key to continue... ");
    gRounds++;
    ShowScore();
    getch();
    if (gEndGame) {
      cleardevice();
      Gprintf( 0, 1, BLACK, WHITE, " End of Game!               ");
      Gprintf( 1, 1, BLACK, WHITE, " Press a key to continue... ");
      ShowScore();
      getch();
      return false;
    }
    StartOver();
    Refresh();
    Gprintf( 1, 1, BLACK, WHITE, " New Round                  ");
  }
  m05Answer[0] = ReadDesktop();
  switch (m05Answer[0]) {
  case 0x1B: // Esc
  case 'e': // Exit
    ProgramDestructor();
    exit( 7 );
    break;
  case 'h': // Help
    m05Answer[1] = ReadMenu(gHelpMenu,HELP_PULLDOWN_COUNT);
    if (m05Answer[1] == 'a') About();
    gChanged = true;
    break;
  default:
    switch (gPhase) {
    case 0:
      switch (m05Answer[0]) {
      case 't': // Take
        if (pTake()) gPhase = 1;
        /* Failure to take repeats Phase 0 */
        gChanged = true;
        break;
      case 'd': // Draw
        if (pDraw()) gPhase = 1;
        /* Failure to draw repeats Phase 0 */
        gChanged = true;
        break;
      case 'r': // Restore
        RestoreStateOfComputer();
        break;
      case 's': // Save
        SaveStateOfComputer();
        break;
      }
      break;
    case 1:
      switch (m05Answer[0]) {
      case 'm': // Meld
        pMeld(false);
        gChanged = true;
        break;
      case 'd': // Discard
        if (pDiscard()) ComputerTurn();
        gChanged = true;
        break;
      }
      break;
    }
  }

  return true;
}

/*

This function closes the graphic environment and clears the text screen.

*/

void far ProgramDestructor() {
  closegraph();
  pd2();
}

/*

This function is the partial destructor that clears the text screen.

*/

void far pd2() {
  textmode( C4350 );
  textcolor( LIGHTGRAY );
  textbackground( BLACK );
  clrscr();
}

/*

This function assists the qsort function call.

*/

int far sort_function( const void *sfunA, const void *sfunB) {
   return( strcmp((char *)sfunA,(char *)sfunB) );
}

// END OF FILE: GCANASTA.CPP

```

---

### Post by cgroza on 2011-07-15
I don't know this game, but are you saying that the Artificial Intelligence of this game is too weak?

---

### Post by machdohvah on 2011-07-16
> **cgroza said:**
> I don't know this game, but are you saying that the Artificial Intelligence of this game is too weak?

Quite right. I have played the game with the cards exposed (via #define TESTING) many times and I cannot see why it refuses to complete canastas when cards are available in its hand and never actually attempts to "go out". It never actually tries to win. Something is wrong.

---

### Post by nvteighen on 2011-07-16
Start from scratch.

I know that may sound rude, but it's what you've got to do. There are a couple of reasons why you haven't been able to solve this in years, which in turn are also the reasons why nobody will be able to help you.

Your code is a mess, mainly because you're not abstracting anything. Almost no function uses parameters and almost none returns a value. Thus you use global variables by default for anything that's used in more than one function. This leads to the following issue: each function's respective behaivor becomes affected by data that's external to its own definition and therefore, you can't say that your functions are "black boxes" that encapsulate some behaivor independently.

Abstraction is nice. Procedural abstraction consists in making each function's behaivor be affected only by the parameters it gets passed. This means that the function's behaivor can be predicted by just looking at its definition, regardless of what happens in other places. Also, good abstraction tries to give each function one single task. All of this leads you to combine functions much easily: their behaivor is known because you've limited the factors that can affect them and by limiting their behaivor to one single task. 

That way, your program will be built by combining small LEGO-like blocks into an increasingly bigger structure, in a managed way. Surprisingly in some places, you do it, but it's in the minority of cases.

But your code is almost impossible to read, because it's got no structure and everything is intertwined and affects everything else. Trying to figure out what everything does is a daunting task, and the fault is not in the reader (I know C very well... read below why I've called the language C and not C++), but in the writer. Also, your variable names are enigmatic, to say the least. That's why it's very unlikely that somebody will show up with some solution for your problem.

Also, keep your functions as general as possible: the way the computer and the player play is actually the same and you can reduce that to one function. The difference is that the computer gets data from an algorithm while the user feeds user input in.

All what I've said should help you in learning Artificial Intelligence algorithms. AI is about tree-searchs, pathfinding methods, heuristic algorithms, etc.; it's a quite challenging field. To do that correctly implies reading about algorithms, about those specific algorithms, know how to traverse a tree data structure or a heap (and know what these are), and know how to abstract things and understand quite general higher-order procedures. It's not trivial to implement these things at all, less in C.

Finally, language. You're not using C++; that's C, with some non-standard extensions, with data structures declared with *class* instead of *struct*, and compiled with an ancient, non-standard, infamous C++ compiler. For your information, stuff like *far* declarations are only Borland-specific. C++ features a lot of features that can help you to write this program much easily: object-oriented programming, high-level built-in data structures, to mention some. You use none of them... actually, I'm not sure if Borland even supports many of the standard STL C++98 features. The irony is is that you're using Ubuntu and you've got g++, the GNU C++ compiler, which is one of the best standard-compliant compilers in the whole market, for free in the repos... and that it allows you to compile programs that run natively on GNU/Linux. Even in the case you wanted to compile something to run on DOS or Windows, there are newer and much better alternatives also available in the Ubuntu repositories.

Of course, rewriting this for GNU/Linux also means that you'll have to learn the system APIs and libraries. conio.h is DOS-specific and IIRC, it doesn't even work on the Windows command shell anymore!

In C++ and lots of other languages (including C itself, but I'll leave that aside), the idea is to use Object-Oriented Programming (OOP), which adds data abstraction to the procedural abstraction I described above. You not only abstract behaivor, but also data into little black boxes. This allows you to create the illusion of "objects" that are associated to some "behaivor". Actually, the *class* keyword is meant to create that...

My advice: (re)learn C++ and use g++ as your compiler and write code on gEdit or any text editor. I highly recommend you to follow this guide: [http://cplusplus.com/doc/tutorial/](http://cplusplus.com/doc/tutorial/) Practice with smaller stuff and try implementing a 2-players hot-seat Canasta game... then, adding the AI would be way much easier. (But mind that you'll have to read a lot).

I hope this wasn't too harsh.

---

### Post by machdohvah on 2011-07-17
I have tried getting anything to work in various g++ compilers with no results at all. Yes, DOS is dead, but I am not intending to sell this to anyone. This is just for my entertainment. It so happens that I actually own a copy of Borland Turbo C++ in the box. The other g++ interfaces do not have extensive help files like the one I own. So, I use a C++ compiler to implement C code. Again, this is not for sale.

I have created a cousin to this code through cannibalizing this one. This cousin is a two-player round robin version that allows the user to play both hands. In the future, I am thinking of creating one for a four player partnership version that allows the user to play all four hands. Again, this is just for my amusement and not for sale.

Maybe I should take all the prefixes out and check all the spelling. Maybe I should change all the "class" entries to "struct". I mean I never intended to use the class device to begin with. I started programming card games back in 1975 with computer tape on a teletype patched into the University's main frame. This is a hobby.

---

### Post by unknownPoster on 2011-07-17
As nvteighen has said, you aren't going to get much help with code like you have written.

Your variable naming is quite cryptic at best. Names like d07 or a10L or however you have them named are not helpful to other readers at all.

You've changed all the structs, to classes, but you really didn't change anything at all. You're not practicing simple standards of Object Oriented Programming. For example, all of your class attributes are public, when they should be private. 

Personally, I don't think anyone will be willing to actually help you with your code simply because it would take so much work to get it to compile with any modern compiler.

---

### Post by nvteighen on 2011-07-17
> **machdohvah said:**
> I have tried getting anything to work in various g++ compilers with no results at all. Yes, DOS is dead, but I am not intending to sell this to anyone. This is just for my entertainment. It so happens that I actually own a copy of Borland Turbo C++ in the box. The other g++ interfaces do not have extensive help files like the one I own. So, I use a C++ compiler to implement C code. Again, this is not for sale.

I have created a cousin to this code through cannibalizing this one. This cousin is a two-player round robin version that allows the user to play both hands. In the future, I am thinking of creating one for a four player partnership version that allows the user to play all four hands. Again, this is just for my amusement and not for sale.

Maybe I should take all the prefixes out and check all the spelling. Maybe I should change all the "class" entries to "struct". I mean I never intended to use the class device to begin with. I started programming card games back in 1975 with computer tape on a teletype patched into the University's main frame. This is a hobby.

I get your point, but I deeply disagree.

You've got a practical problem: you haven't been able to fix this in years. So, the problem here is not whether you want to sell this game or not or if this is for your own amusement. It's just that you've written a program in such a convoluted way that now not even you know how to add or fix some functionality to it. If your program actually worked, you might have had the "But it works!" excuse, but it doesn't and you're been trapped like this since ages. (Sincerely, I admire your willpower and patience).

The techniques I told you about (which the C++ tutorial I pointed you to also insists on) were developed in time as means for achieving clarity and avoiding exactly the practical problem you have. They're not just theoretically elegant devices nor "The Only Right Way" dictated by some guru, but well-proven ways to keep track of one's own code.

I'm also a hobbyist; don't be confused by the two projects on my sig. In fact, AFAIK most people in these forums aren't professional programmers (most Ubuntu developers aren't either), but CS students or people interested on programming (like myself; I'm a linguist). The reason why one sticks to abstraction, data encapsulation, algorithms, etc., is because it provides clarity for oneself and for others that might have to read your code for whatever reason (e.g. posting it here).

And about "C compiled with a C++ compiler"... It's fairly common, due to some very bad C++ tutorials there are available. Ok, you're free to do that, because it's possible, but you're missing the point of C++. It's also true that Borland doesn't support much of the C++98 features, so you can't have pretty good stuff like STL vectors, strings, etc.... and mind that I personally hate C++ as much as I can (and avoid it as much as I can...).

FYI: to make g++ work, which is a fairly trivial thing to do, look at these subforums' Stickies.

You're free to do whatever you like, though.

---

### Post by machdohvah on 2011-07-18
> **nvteighen said:**
> I get your point, but I deeply disagree.

...

FYI: to make g++ work, which is a fairly trivial thing to do, look at these subforums' Stickies.

You're free to do whatever you like, though.

I happen to like the old fashioned structured programming. I do not understand the concept of "Object Oriented" anything. A program should be straight forward. The code that follows is changed by removing all of the prefixes and changed all of the "class" to "struct". I am working on (and completed) a two-player version that is a round-robin affair. The user plays both hands as this eliminates the need for AI. I will then work on a four-player partnership round-robin version.

```


#define PROGNAME "GCANASTA"
#define VERSION "17Jul2011"
#define AUTHOR "Michael Flower"

/*

New program (rendered here) ...

GCANASTA.CPP graphic version with entire re-write.

24Nov2007 This started life as a character based system with mouse
attached. That program had too many bugs in it.

26Jan2008 Finished a working game with computer player logic.

29Aug2009 Corrected ComputerTurn to check EndRound at beginning.

30Aug2009 Corrected errors in ComputerTurn.

31Aug2009 There are several problems. Something in ComputerTurn is now
producing an endless loop and I counted ten sevens during play. Nasty!
Decided to remove the DOS SORT calls and replace them with qsort. The
computer locks up when player takes successfully on the first move.

01Sep2009 Tried to OVERLAY this thing but have yet to produce an OVR file.
The computer hand is corrupted upon melding. It appearently is erasing the
wrong cards after it melds the correct ones. Bug corrected: incorrect index
reference.

06Sep2009 Removed all penalties in figuring the score.

12Sep2009 Moved the Meld menu to left edge. Added Save and Restore.

31Oct2010 Reprogrammed the menus.

07Nov2010 Removed conditional on cOutCapabile.

08Nov2010 Changed condition from <= 2 to < 1. gpMeldedBefore and
gcMeldedBefore cancelled between rounds.

14Jul2011 Removed all "far" references as I started to compile this
again in "dosbox" in root terminal with Ubuntu 10.10 operating system.
Introduced NUMBER_CANASTA_OUT, NUMBER_CARDS_DRAW, gpHandCardCount,
and gcHandCardCount. Corrected problem of one card in hand left with
respect to NUMBER_CANASTA_OUT during discard. Created pCalcFirstMeld
on Status Line.

15Jul2011 Returned "far" references to data and functions for it was
over-running its memory. Affixed initials before local variable for
garrentee of seperation. g- = global.

17Jul2011 Following advice from contributers on-line, I replaced "class"
with "struct" and removed the prefixes from each function.

  NOTE: All rules of Canasta in Hoyle are followed. This is the Two-Hand
Canasta variation. "Hoyle's Rules of Games" by Albert H Morehead and
Geoffrey Mott-Smith, revised and updated by Philip D Morehead, Dec2001
edition, page 140.

The definition of TESTING is only needed while debugging the program.
The definition of USE_MOUSE is only needed if the mouse is needed.

*/

#define TESTING
// #define USE_MOUSE

#include <conio.h>
#include <ctype.h>
#include <graphics.h>
#include <stdarg.h>
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <time.h>

/*

Compile with "MLFMOUSE.CPP". This program uses the mouse object
developed purely from interrupts in assembly code. "MouseInfo"
structure is included there.

*/

#ifdef USE_MOUSE
#include "mlfmouse.h"
struct MouseInfo gMouseInformation = { 0, 0, 0, 0, 0 };
#endif

#define DECK_SIZE 108
#define DESKTOP_BUTTON_COUNT 6
#define DISCARD_PULLDOWN_COUNT 15
#define EMPTY -1
#define GAME_PULLDOWN_COUNT 1
#define HELP_PULLDOWN_COUNT 1
#define MAX_ROUNDS 8
#define MELD_DEPTH 15
#define MELD_LOCATIONS 12
#define MELD_PULLDOWN_COUNT 15
#define NATURAL_RANK_PULLDOWN_COUNT 11
#define NUMBER_CANASTA_OUT 2
#define NUMBER_CARDS_DRAW 2
#define STATUS_FOR 14
#define STATUS_BACK 6
#define STATUS_LINE 59
#define STOCK_COLUMN 30
#define STOCK_ROW 24

/*

Eventually, these two will be the current directory.

*/

#define PATH_TO_BGI "\\TC\\BGI"
// #define PATH_TO_BGI ""
#define PATH_TO_CARDS "\\MYDOCS\\TC\\CARDS\\PXL\\"
// #define PATH_TO_CARDS ""

enum {COMPUTER, PLAYER, NUM_PLAYERS};
enum bool {false, true};

/*

Cards are shuffled in this program by sorting on random numbers. The
Title field is only two characters long. Rank and Suit are needed for
sorting the hands. Rank is a number that is in line with its rank in
the game while Title contains the name of the card. This seperation is
needed for the jokers. All arrays with +1 allocation are there for
avoiding sort aliocation errors.

*/

struct cCard {
  char Shuffle[4], Title[3], Rank, Suit;
  int Value;
  bool IsWild;
};

cCard far gCard[DECK_SIZE+1];

/*

New cards in the hand are placed at the end of the hand and later
sorted. The hand only holds the rank and the card index
for all the other information is static with the card itself.

*/

struct cHand {
  char Rank; // for sorting
  int Index;
  bool Selected;
};

cHand far gHand[NUM_PLAYERS+1][DECK_SIZE+1];

/*

All threes are in Meld0. Meld1 thru MELD_LOCATIONS is in order of
rank string minus the wild cards.

*/

struct cMeld {
  bool IsBook;
  bool HasWild;
  int Position[MELD_DEPTH+1];
};

cMeld far gMeld[NUM_PLAYERS+1][MELD_LOCATIONS+1];

/*

The desktop menu has two incarnations, one for each phase.

*/

struct cMenu {
  char letter;
  char *caption;
  int row1, col1, row2, col2;
};

cMenu far gDesktop[2][DESKTOP_BUTTON_COUNT+1] = {
  {
    {'t', " Take ",    0, 0, 0, 5},
    {'d', " Draw ",    0, 6, 0,11},
    {'s', " Save ",    0,12, 0,17},
    {'r', " Restore ", 0,18, 0,26},
    {'e', " Exit   ",  0,27, 0,34},
    {'h', " Help ",    0,74, 0,79}
  }, {
    {'m', " Meld ",    0, 0, 0, 5},
    {'d', " Discard ", 0, 6, 0,14},
    {'d', "      ",    0,15, 0,20},
    {'d', "         ", 0,21, 0,29},
    {'e', " Exit   ",  0,30, 0,37},
    {'h', " Help ",    0,74, 0,79}
  }
};

/*

The second choices are the only things in the pull-down.

*/

cMenu far gDiscardMenu[DISCARD_PULLDOWN_COUNT+1] = {
  {'3'," 3 Three ", 2, 6, 2,14},
  {'4'," 4 Four  ", 3, 6, 3,14},
  {'5'," 5 Five  ", 4, 6, 4,14},
  {'6'," 6 Six   ", 5, 6, 5,14},
  {'7'," 7 Seven ", 6, 6, 6,14},
  {'8'," 8 Eight ", 7, 6, 7,14},
  {'9'," 9 Nine  ", 8, 6, 8,14},
  {'t'," T Ten   ", 9, 6, 9,14},
  {'j'," J Jack  ",10, 6,10,14},
  {'q'," Q Queen ",11, 6,11,14},
  {'k'," K King  ",12, 6,12,14},
  {'a'," A Ace   ",13, 6,13,14},
  {'2'," 2 Two   ",14, 6,14,14},
  {'z'," Z Joker ",15, 6,15,14},
  {'x'," X DONE  ",16, 6,16,14}
};

cMenu far gMeldMenu[MELD_PULLDOWN_COUNT+1] = {
  {'3'," 3 Three ", 2, 1, 2, 9},
  {'4'," 4 Four  ", 3, 1, 3, 9},
  {'5'," 5 Five  ", 4, 1, 4, 9},
  {'6'," 6 Six   ", 5, 1, 5, 9},
  {'7'," 7 Seven ", 6, 1, 6, 9},
  {'8'," 8 Eight ", 7, 1, 7, 9},
  {'9'," 9 Nine  ", 8, 1, 8, 9},
  {'t'," T Ten   ", 9, 1, 9, 9},
  {'j'," J Jack  ",10, 1,10, 9},
  {'q'," Q Queen ",11, 1,11, 9},
  {'k'," K King  ",12, 1,12, 9},
  {'a'," A Ace   ",13, 1,13, 9},
  {'2'," 2 Two   ",14, 1,14, 9},
  {'z'," Z Joker ",15, 1,15, 9},
  {'x'," X DONE  ",16, 1,16, 9}
};

cMenu far gNatualRankMenu[NATURAL_RANK_PULLDOWN_COUNT+1] = {
  {'4'," 4 Four  ", 3, 6, 3,14},
  {'5'," 5 Five  ", 4, 6, 4,14},
  {'6'," 6 Six   ", 5, 6, 5,14},
  {'7'," 7 Seven ", 6, 6, 6,14},
  {'8'," 8 Eight ", 7, 6, 7,14},
  {'9'," 9 Nine  ", 8, 6, 8,14},
  {'t'," T Ten   ", 9, 6, 9,14},
  {'j'," J Jack  ",10, 6,10,14},
  {'q'," Q Queen ",11, 6,11,14},
  {'k'," K King  ",12, 6,12,14},
  {'a'," A Ace   ",13, 6,13,14}
};

cMenu far gHelpMenu[HELP_PULLDOWN_COUNT+1] = {
  {'a'," About GCANASTA ", 2,63, 2,78}
};

/*

Miscellanious globals

*/

int    gBonusPoints[MAX_ROUNDS+1][NUM_PLAYERS+1];
char * gCardBackFileName = "FILENAME.EXT";
bool   gChanged = true;
int    gDiscard[DECK_SIZE+1];
bool   gEndGame = false;
bool   gEndRound = false;
int    gLastCB = 0;
int    gMeldPoints[MAX_ROUNDS+1][NUM_PLAYERS+1];
int    gNextCardInStock = EMPTY;
int    gPhase = 0;
char * gRankString = "3456789TJQKA2Z";
int    gRounds = 1;
int    gScore[MAX_ROUNDS+1][NUM_PLAYERS+1];
int    gStock[DECK_SIZE+1];
char * gSuitString = "HDSC";
int    gTextHeight;
int    gTextWidth;
int    gTopPile;

int    gcCanastaCount = 0;
int    gpCanastaCount = 0;
int    gcHandCardCount = 0;
int    gpHandCardCount = 0;
bool   gcMeldedBefore = false;
bool   gpMeldedBefore = false;
bool   gBlack3PreviousTurn = false;
int    gNextAvailableMeldPit = 0;
int    gWildsOnTable = 0;
int    gKnatsOnTable = 0;
bool   gWildInDiscardPile = false;

char   gS[80] = "";
char   gRecord[DECK_SIZE][80];

/*


Function declarations (c- = computer; p- = player)

*/

void far Abort(int,char *);
void far About();
int  far pCalcFirstMeld();
void far ComputerTurn();
void far DeselectAllInHand(int);
void far cDiscard(int,int);
bool far pDiscard();
void far DisplayCard(int,int,int,bool);
bool far cDraw();
bool far pDraw();
int  far DrawCard(int);
void far FigureScore(int);
int  far cFindBlackThree();
int  far cFindMeldPit(char);
int  far cFindNaturalLowCountRank();
int  far cFindWild();
bool far cFirstMeld();
void far GetPixelsFromFile(char *,int,int,bool);
void far Gprintf(int,int,int,int,char *,...);
void far HideMenu(cMenu *,int);
bool far IsRedThree(int,int);
char far pMeld(bool ForTake);
void far cMeldAllNaturals();
int  far cMinLegalMeld();
bool far pMinLegalMeld(bool);
void far NextCardBack();
void far cOutCapabile();
char far ReadDesktop();
char far ReadMenu(cMenu *,int);
void far Refresh();
void far RestoreBehindWindow(char *,int,int,int,int);
void far RestoreStateOfComputer();
void far SaveBehindWindow(char *,int,int,int,int);
void far SaveStateOfComputer();
int  far SelectCardInHand(int,char);
void far ShowMelds(int,int);
void far ShowMenu(cMenu *,int);
void far ShowScore();
void far ShuffleDeck();
void far SortHand(int);
void far StartOver();
bool far pTake();
bool far cTryTakeDiscard();
void far WaitASec();
int  far cWhereInHand(int);

void far ProgramConstructor();
bool far MainLoop();
void far ProgramDestructor();
void far pd2();

int  far sf( const void *, const void *);

/*

Program entry point. Calls the constructor, maintains the main loop,
and then calls the destructor.

*/

void main() {
  ProgramConstructor();
  while (MainLoop());
  ProgramDestructor();
}

/*

This function alerts the user what line called the function and for
what reason, calls the destructor, then aborts the program.

*/

void far Abort(int l, char *s) {
  cleardevice();
  Gprintf(1,1,YELLOW,BLACK,"%s aborted on line %d for this reason:",
    PROGNAME,l);
  Gprintf(2,1,YELLOW,BLACK,"%s",s);
  Gprintf(3,1,YELLOW,BLACK,"Press a key to continue...");
  getch();
  ProgramDestructor();
}

/*

This function shows a window that shows an announcement of information
about the program.

*/

void far About() {
  int i=0;

  SaveBehindWindow("ABTSAVE.DTA",25,26,38,54);
  Gprintf(25,26, BLACK, WHITE, "ÚÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄ¿");
  Gprintf(26,26, BLACK, WHITE, "³ %s                 ³%c",PROGNAME,
    0xB2);
  Gprintf(27,26, BLACK, WHITE, "³ %s                ³%c", VERSION,
    0xB2);
  Gprintf(28,26, BLACK, WHITE, "ÃÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄŽ%c",0xB2);
  Gprintf(29,26, BLACK, WHITE, "³ This program was written ³%c",0xB2);
  Gprintf(30,26, BLACK, WHITE, "³ by %s        ³%c",AUTHOR,0xB2);
  Gprintf(31,26, BLACK, WHITE, "³ and is intended as a     ³%c",0xB2);
  Gprintf(32,26, BLACK, WHITE, "³ demonstraion only and is ³%c",0xB2);
  Gprintf(33,26, BLACK, WHITE, "³ not for sale or lease to ³%c",0xB2);
  Gprintf(34,26, BLACK, WHITE, "³ anyone.                  ³%c",0xB2);
  Gprintf(35,26, BLACK, WHITE, "ÃÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄŽ%c",0xB2);
  Gprintf(36,26, BLACK, WHITE, "³ For the rules, see Hoyle ³%c",0xB2);
  Gprintf(37,26, BLACK, WHITE, "ÀÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÙ%c",0xB2);
  for (i=27;i<=54;i++) {
    Gprintf(38, i, BLACK, WHITE, "%c",0xB2);
  }
  ReadDesktop();
  RestoreBehindWindow("ABTSAVE.DTA",25,26,38,54);
}

/*

This function simulates the opponent player. It looks for a black
three, remembers if there was a black three in the previous turn and if
the discard pile has been taken in this turn. Depending on the result,
it tries to take the discard pile. Failing to take the discard pile, he
draws two cards. Depending on if he was finished with the previous
black three, he melds all the naturals he can. He checks to see if he
is capable to "go out". He checks for a first meld. He looks for a
black three, a wild, or a natural to discard ending his turn.

*/

void far ComputerTurn() {
  int BlackThree = EMPTY;
  bool ComputerTake = false;
  int Wild = EMPTY;
  int DeckIndex = 0;

  if (gEndRound) return;
  Refresh();
  BlackThree = cFindBlackThree();
  if (!gBlack3PreviousTurn) {
    if (cTryTakeDiscard()) {
      ComputerTake = true;
    }
  }
  if (!ComputerTake) {
    if (cDraw()) {
      gBlack3PreviousTurn = false;
    }
  }
  if ( !gcMeldedBefore ) gcMeldedBefore = cFirstMeld();
  if (gcMeldedBefore) cMeldAllNaturals();
// 07Nov2010 Removed conditional on cOutCapabile.
  cOutCapabile();
  Wild = cFindWild();
  if ( BlackThree != EMPTY ) {
    DeckIndex = BlackThree;
    cDiscard( DeckIndex, cWhereInHand( DeckIndex ));
    gBlack3PreviousTurn = true;
  }
  else {
    if ( !(gBlack3PreviousTurn) && !(gWildInDiscardPile) && (Wild != EMPTY) ) {
      DeckIndex = Wild;
      cDiscard( DeckIndex, cWhereInHand( DeckIndex ));
      gWildInDiscardPile = true;
    }
    else {
      DeckIndex = cFindNaturalLowCountRank();
      cDiscard( DeckIndex, cWhereInHand( DeckIndex ));
    }
  }
  gPhase = 0;
}

/*

This function de-selects all the cards in the specified hand.

*/

void far DeselectAllInHand(int Who) {
  int i=0;

  for (;i<DECK_SIZE;i++)
    gHand[Who][i].Selected = false;
}

/*

This function discards specified card from specified location in
the computer hand.

*/

void far cDiscard( int Which, int Where ) {
  if ( gcHandCardCount == 1)
    if ( gcCanastaCount < NUMBER_CANASTA_OUT ) return;

  gTopPile++;
  gDiscard[gTopPile] = Which;
  gHand[COMPUTER][Where].Index = EMPTY;
  gHand[COMPUTER][Where].Rank = '~';
  gHand[COMPUTER][Where].Selected = false;
  gcHandCardCount--;
  SortHand(COMPUTER);
}

/*

This function checks for minimum/legal meld, waits on the user to
specify a card for discard from his hand, removes the card from the
hand, places the card in the discard pile, sorts the hand in order of
rank, and checks for an empty hand declairing the round over.

*/

bool far pDiscard() {
  char a = ' ';
  int c, h;

  c=h=0;
  if (!(pMinLegalMeld(false))) return false;
/*

14Jul2011 Special case: If there is only one card left, disallow if
there are less then the NUMBER_CANASTA_OUT.

*/
  if ( gpHandCardCount == 1)
    if ( gpCanastaCount < NUMBER_CANASTA_OUT ) return false;

  for (;;) {
    a = ReadMenu(gDiscardMenu,DISCARD_PULLDOWN_COUNT);
    if (a == 0x0D) return false;
    a = toupper(a);
    if (a == 'X') return false;
    c = SelectCardInHand(PLAYER,a);
    if (c != EMPTY) break;
  }
  h = gHand[PLAYER][c].Index;
  gHand[PLAYER][c].Index = EMPTY;
  gHand[PLAYER][c].Rank = '~';
  gHand[PLAYER][c].Selected = false;
  gpHandCardCount--;
  gTopPile++;
  gDiscard[gTopPile] = h;
  SortHand(PLAYER);
  if (gpHandCardCount <= 0) gEndRound = true;

  return true;
}

/*

This function displays the selected card at specified row and col. It
needs to know if it is sideways or not.

*/

void far DisplayCard( int Card, int Row, int Col, bool Sideways ) {
  sprintf( gS, "%s.PXL", gCard[Card].Title );
  GetPixelsFromFile( gS, Row, Col, Sideways );
}

/*

Computer draws NUMBER_CARDS_DRAW cards storing the index and rank. It
shows a card back for each card as it processes. It notifies the caller
if it failed to draw a card.

*/

bool far cDraw() {
  int c=0,i;

for (i=0;i<NUMBER_CARDS_DRAW;i++) {
  c = DrawCard(COMPUTER);
  if (c == EMPTY) return false;
  gHand[COMPUTER][DECK_SIZE-(1+i)].Index = c;
  gHand[COMPUTER][DECK_SIZE-(1+i)].Rank = gCard[c].Rank;
  gcHandCardCount++;
#ifdef TESTING
  DisplayCard(c,STOCK_ROW,STOCK_COLUMN-4+(2*i),false);
#else
  GetPixelsFromFile( gCardBackFileName, STOCK_ROW, STOCK_COLUMN-4+(2*i),
    false );
#endif
}

  SortHand(COMPUTER);
  WaitASec();

  return true;
}

/*

User draws NUMBER_CARDS_DRAW cards storing the index and rank. It shows
a card face for each card as it processes. It notifies the caller if it
failed to draw a card.

*/

bool far pDraw() {
  int c=0, i;

  for (i=0;i<NUMBER_CARDS_DRAW;i++) {
    c = DrawCard(PLAYER);
    if (c == EMPTY) return false;
    gHand[PLAYER][DECK_SIZE-(1+i)].Index = c;
    gHand[PLAYER][DECK_SIZE-(1+i)].Rank = gCard[c].Rank;
    gpHandCardCount++;
    DisplayCard(c,STOCK_ROW,STOCK_COLUMN-4+(2*i),false);
  }

  SortHand(PLAYER);
  WaitASec();

  return true;
}

/*

This function draws a card into the specified hand. It checks for an
empty stock pile, draws a card from stock, checks for red threes (Meld0
is for threes, red and black) drawing a replacement card if needed.

*/

int far DrawCard(int Who) {
  int Result;
  bool Continuing = true;

  Result=0;
  while (Continuing) {
    if (gNextCardInStock == EMPTY) return EMPTY;
    Continuing = false;
    Result = gStock[gNextCardInStock];
    gStock[gNextCardInStock] = EMPTY;
    gNextCardInStock--;
    if (IsRedThree(Who, Result)) Continuing = true;
  }
  return Result;
}

/*

This function figures the score at the end of the round. Awards bonus
points, awards meld points, subtracts sorted hand, storing the running
total.

*/

void far FigureScore(int r) {
  int c,i,j,k;

  c=i=j=k=0;
  for (i=0;i<NUM_PLAYERS;i++) {
    gBonusPoints[r][i] = 0;
    for (j=1;j<MELD_LOCATIONS;j++) {
      if (gMeld[i][j].IsBook) {
        if(gMeld[i][j].HasWild)
             gBonusPoints[r][i] += 300; // black canasta
        else gBonusPoints[r][i] += 500; // red canasta
      }
    }

    for (j=0,k=0;j<MELD_DEPTH;j++) { // count red threes
      c = gMeld[i][0].Position[j];
      if (c == EMPTY) {
        break;
      }
      if ((gCard[c].Title[1] == 'H') ||
          (gCard[c].Title[1] == 'D')) {
        k++;
      }
    }
    gBonusPoints[r][i] += (k*100); // red three award

    gMeldPoints[r][i] = 0; // figure meld points
    for (j=0;j<MELD_LOCATIONS;j++) {
      for (k=0;k<MELD_DEPTH;k++) {
        c = gMeld[i][j].Position[k];
        if (c == EMPTY) {
          break;
        }
        gMeldPoints[r][i] += gCard[c].Value;
      }
    }

    for (j=0;j<DECK_SIZE;j++) { // deduct for cards in hand
      c = gHand[i][j].Index;
      if (c == EMPTY) {
        if (j==0) { // award 100 for going out
          gBonusPoints[r][i] += 100;
        }
        break;
      }
      else {
        gMeldPoints[r][i] -= gCard[c].Value;
      }
    }

    gScore[r][i] = gBonusPoints[r][i] + gMeldPoints[r][i];
    if (r > 0) gScore[r][i] += gScore[r-1][i];
  }
  if (gScore[r][PLAYER]   >= 5000) gEndGame = true;
  if (gScore[r][COMPUTER] >= 5000) gEndGame = true;
  if (r>= MAX_ROUNDS-1)           gEndGame = true;
}

/*

This function looks for a black three in computer hand sorted in order
by rank. Returns EMPTY if failed.

*/

int far cFindBlackThree() {
  int i;
  int Result = EMPTY;
  int DeckIndex;
  char a,b;

  for (i=0; i<DECK_SIZE; i++) {
    DeckIndex = gHand[COMPUTER][i].Index;
    if ( DeckIndex == EMPTY ) break;
    a = gCard[DeckIndex].Title[0];
    b = gCard[DeckIndex].Title[1];
    if ( a == '3' ) {
      if ((b == 'S') || (b == 'C')) {
        Result = DeckIndex;
        break;
      }
    }
  }

  return Result;
}

/*

This function find an the right meld pit for the computer hand for a
given natural to meld. Returns EMPTY if not found.

*/

int far cFindMeldPit( char NatInMeld) {
  int i, j;
  char RankOfCardInList;
  int Result = EMPTY;
  int DeckIndex;

  gNextAvailableMeldPit = 0;
  gWildsOnTable = 0;
  gKnatsOnTable = 0;
  for (i=1; i<MELD_LOCATIONS; i++) {
    for ( j=0; j<MELD_DEPTH; j++ ) {
      DeckIndex = gMeld[COMPUTER][i].Position[j];
      if ( DeckIndex == EMPTY ) break;
      RankOfCardInList = gCard[DeckIndex].Title[0];
      if (( RankOfCardInList != 'Z' ) && ( RankOfCardInList != '2' )) {
        if ( NatInMeld == RankOfCardInList ) {
          Result = i;
          break;
        }
        else break;
      }
    }
    if ( Result != EMPTY ) break;
    if (( j == 0 && DeckIndex == EMPTY )) break;
  }
  if ( Result == EMPTY ) gNextAvailableMeldPit = i;
  else {
    for ( j=0; j<MELD_DEPTH; j++ ) {
      DeckIndex = gMeld[COMPUTER][Result].Position[j];
      if ( DeckIndex == EMPTY ) break;
      switch ( gCard[DeckIndex].Title[0] ) {
      case 'Z':
      case '2':
        gWildsOnTable++;
        break;
      default:
        gKnatsOnTable++;
      }
    }
  }

  return Result;
}

/*

This function finds the lowest rank and the lowest count of a natural
to discard from the computer hand.

*/

int far cFindNaturalLowCountRank() {
  int Result;
  int i, j;
  char RankOfCardInHand, *ptr;
  int NatCount[11];
  int DeckIndex;

  for (i=0; i<11; i++) NatCount[i] = 0;
  for (i=0; i<DECK_SIZE; i++) {
    DeckIndex = gHand[COMPUTER][i].Index;
    if ( DeckIndex == EMPTY ) break;
    RankOfCardInHand = gCard[DeckIndex].Title[0];
    ptr = strchr( gRankString, RankOfCardInHand );
    switch ( RankOfCardInHand ) {
    case 'Z':
    case '2':
    case '3':
      break;
    default:
      NatCount[(int) (ptr-gRankString)-1]++;
    }
  }
  RankOfCardInHand = ' ';
  for ( i=1; i<=8; i++) {
    for ( j=0; j<11; j++ ) {
      if ( NatCount[j] == i ) {
        RankOfCardInHand = gRankString[j+1];
        break;
      }
    }
    if ( RankOfCardInHand != ' ' ) break;
  }
  for (i=0; i<DECK_SIZE; i++) {
    DeckIndex = gHand[COMPUTER][i].Index;
    if ( gCard[DeckIndex].Title[0] == RankOfCardInHand ) {
      Result = DeckIndex;
      break;
    }
  }

  return Result;
}

/*

This function looks for a wild in the computer hand.

*/

int far cFindWild() {
  char RankOfCardInList;
  int i;
  int Result = EMPTY;
  int DeckIndex;

  for (i=0; i<DECK_SIZE; i++) {
    DeckIndex = gHand[COMPUTER][i].Index;
    if ( DeckIndex == EMPTY ) break;
    RankOfCardInList = gCard[DeckIndex].Title[0];
    if (( RankOfCardInList == '2' ) ||
        ( RankOfCardInList == 'Z' )) {
      Result = DeckIndex;
      break;
    }
  }

  return Result;
}

/*

This function attempts to meld from the computer hand for the first
time.

*/

bool far cFirstMeld() {
  int CardList[20];
  int i, j, k;
  int NatCount[11];
  int NatList[8];
  int NatInList;
  char *ptr;
  char RankOfCardInList;
  bool Result = false;
  int Score;
  int WildList[12];
  int WldInHand = 0;
  int DeckIndex;
  int MeldPit = 0;
  int MinMeld = cMinLegalMeld();

  for (i=0; i<20; i++) CardList[i] = EMPTY;
  for (i=0; i<11; i++) NatCount[i] = 0;
  for (i=0; i<8; i++) NatList[i] = EMPTY;
  for (i=0; i<12; i++) WildList[i] = EMPTY;
  for (i=0; i<DECK_SIZE; i++) {
    DeckIndex = gHand[COMPUTER][i].Index;
    if ( DeckIndex == EMPTY ) break;
    RankOfCardInList = gCard[DeckIndex].Title[0];
    ptr = strchr( gRankString, RankOfCardInList );
    switch ( RankOfCardInList ) {
    case 'Z':
    case '2':
    case '3':
      break;
    default:
      NatCount[(int) (ptr-gRankString)-1]++;
    }
  }
  RankOfCardInList = ' ';
  for ( i=8; i>=2; i--) {
    for ( j=10; j>=0; j-- ) {
      if ( NatCount[j] == i ) {
        RankOfCardInList = gRankString[j+1];
        Score = 0;
        NatInList = 0;
        for ( k=0; k<DECK_SIZE; k++ ) {
          DeckIndex = gHand[COMPUTER][k].Index;
          if ( DeckIndex == EMPTY ) break;
          if ( gCard[DeckIndex].Title[0] == RankOfCardInList ) {
            CardList[NatInList] = DeckIndex;
            NatList[NatInList++] = DeckIndex;
            Score += gCard[DeckIndex].Value;
            if ( Score >= MinMeld ) break;
          }
        }
        if ( Score >= MinMeld ) Result = true;
        else {
          Result = false;
          for ( k=0; k<DECK_SIZE; k++ ) {
            DeckIndex = gHand[COMPUTER][k].Index;
            if ( DeckIndex == EMPTY ) break;
            if ( gCard[DeckIndex].Title[0] == 'Z' ) {
              CardList[NatInList+WldInHand] = DeckIndex;
              WildList[WldInHand++] = DeckIndex;
              Score += gCard[DeckIndex].Value;
              if ( Score >= MinMeld ) {
                Result = true;
                break;
              }
            }
          }
          if ( !Result ) {
            for ( k=0; k<DECK_SIZE; k++ ) {
              DeckIndex = gHand[COMPUTER][k].Index;
              if ( DeckIndex == EMPTY ) break;
              if ( gCard[DeckIndex].Title[0] == '2' ) {
                CardList[NatInList+WldInHand] = DeckIndex;
                WildList[WldInHand++] = DeckIndex;
                Score += gCard[DeckIndex].Value;
                if ( Score >= MinMeld ) {
                  Result = true;
                  break;
                }
              }
            }
          }
          if ( NatInList <= WldInHand ) Result = false;
        }
        if ( Result ) break;
        else {
          NatInList = 0; WldInHand = 0;
          for ( k=0; k<20; k++ ) CardList[k] = EMPTY;
          for ( k=0; k<8; k++ ) NatList[k] = EMPTY;
          for ( k=0; k<12; k++ ) WildList[k] = EMPTY;
        }
      }
    }
    if ( Result ) break;
  }
  if ( Result ) {
    switch (RankOfCardInList) {
    case '4': MeldPit =  1; break;
    case '5': MeldPit =  2; break;
    case '6': MeldPit =  3; break;
    case '7': MeldPit =  4; break;
    case '8': MeldPit =  5; break;
    case '9': MeldPit =  6; break;
    case 'T': MeldPit =  7; break;
    case 'J': MeldPit =  8; break;
    case 'Q': MeldPit =  9; break;
    case 'K': MeldPit = 10; break;
    case 'A': MeldPit = 11; break;
    }
    for ( j=0; j<WldInHand; j++ ) {
      DeckIndex = WildList[j];
      if ( DeckIndex == EMPTY ) break;
      gMeld[COMPUTER][MeldPit].Position[j] = DeckIndex;
    }
    for ( k=0; k<NatInList; k++ ) {
      DeckIndex = NatList[k];
      if ( DeckIndex == EMPTY ) break;
      gMeld[COMPUTER][MeldPit].Position[j+k] = DeckIndex;
    }
    for (i=0; i<20; i++) {
      DeckIndex = CardList[i];
      if ( DeckIndex == EMPTY ) break;
      for ( j=0; j<DECK_SIZE; j++ ) {
        DeckIndex = gHand[COMPUTER][j].Index;
        if ( DeckIndex == CardList[i] ) break;
      }
      gHand[COMPUTER][j].Index = EMPTY;
      gHand[COMPUTER][j].Rank = '~';
      gHand[COMPUTER][j].Selected = false;
      gcHandCardCount--;
    }
    SortHand(COMPUTER);
  }

  return Result;
}

/*

This function looks for hex representation in an ascii file. CRLF is
interpreted as the end of line. Each hex digit represents the color
values of 0 through 15. Other values are skipped. The color is then
placed on the screen pixle by pixle. All of the files must be present
for this program to run.

*/

void far GetPixelsFromFile(char *FileName, int Row, int Col, bool Sideways) {
  int Xref = Col*gTextWidth;
  int Yref = Row*gTextHeight;
  int x, y, Color;
  FILE *InFile;
  int Width;
  char s[640]="";

  x=y=Color=Width=0;
  sprintf(s,"%s%s",PATH_TO_CARDS,FileName);
  if ( (InFile = fopen(s, "rb")) == NULL ) {
    sprintf(s,"File not found: %s%s",PATH_TO_CARDS,FileName);
    Abort(__LINE__,s);
    exit( 1 );
  }
  else {

  fgets(s, 640, InFile );
  while ( !feof(InFile) ) {
    Width = strlen(s);
    for (x=0; x<Width; x++) {
      Color = EMPTY;
      switch (s[x]) {
      case '0': Color =  0; break;
      case '1': Color =  1; break;
      case '2': Color =  2; break;
      case '3': Color =  3; break;
      case '4': Color =  4; break;
      case '5': Color =  5; break;
      case '6': Color =  6; break;
      case '7': Color =  7; break;
      case '8': Color =  8; break;
      case '9': Color =  9; break;
      case 'A': Color = 10; break;
      case 'B': Color = 11; break;
      case 'C': Color = 12; break;
      case 'D': Color = 13; break;
      case 'E': Color = 14; break;
      case 'F': Color = 15;
      }
      if (Sideways) {
        if (Color != EMPTY) putpixel( y+312,278-x, Color );
      }
      else {
        if (Color != EMPTY) putpixel( x+Xref, y+Yref, Color );
      }
    }
    y++;
    fgets(s, 640, InFile );
  }
  fclose( InFile );

  }
}

/*

This function is intended to be a graphic replacement for a combination
of gotoxy, textcolor, textbachground, and cprintf using va_list,
vsprintf, setcolor, and outtextxy.

*/

void far Gprintf( int Row, int Col, int ForColor, int BackColor,
    char *FormatString, ... ) {
  va_list ArgumentPointer;
  int i=0;

  va_start( ArgumentPointer, FormatString );
  vsprintf( gS, FormatString, ArgumentPointer );
  char BackStr[2] = {0xDB,0x00};
  setcolor( BackColor );
  for (; i<strlen( gS ); i++)
    outtextxy( (Col+i) * gTextHeight, Row * gTextWidth, BackStr );
  setcolor( ForColor );
  outtextxy( Col * gTextHeight, Row * gTextWidth, gS );
  va_end( ArgumentPointer );
}

/*

This function is used to hide the menu after a selection is made.

*/

void far HideMenu(cMenu* PullDown, int Entries) {
  int MenuWidth = strlen(PullDown[0].caption);
  int Top = PullDown[0].row1-1;
  int Left = PullDown[0].col1-1;
  int Bottom = PullDown[Entries-1].row1+1;
  int Right = PullDown[Entries-1].col1+MenuWidth;

  RestoreBehindWindow("MENUBACK.DTA", Top, Left, Bottom+1, Right+1);
}

/*

Test for red three and move to Meld0

*/

bool far IsRedThree(int Who, int n) {
  int d;
  bool Result = false;

  if (gCard[n].Title[0] == '3') {
    switch(gCard[n].Suit) {
    case 'H': case 'D': // Red three
      for (d=0;d<MELD_DEPTH;d++) {
        if (gMeld[Who][0].Position[d] == EMPTY) {
          gMeld[Who][0].Position[d] = n;
          break;
        }
      }
      Result = true;
      break;
    }
  }
  return Result;
}

/*

Player Meld: Builds a queue of cards from the user selections
displaying a dot for each selection as it goes. It seperates the wilds
from the naturals, allows for only one rank, checks for all wilds and
assigns rank from the user, reverses all selection if failed, includes
the top of the discard pile if for taking, moves cards from the user
hand to his meld pit and returns the rank or blank. Rules for
individual meld are that naturals and wilds add to three cards and that
there are equal or more naturals then wilds in the melded result.

*/

char far pMeld(bool ForTake) {
  int b,c,i,j,n,p,q,r,t,w;
  int Queue[MELD_DEPTH];
  char a,RankOfQueue;

  b=c=n=p=q=r=t=w=0;
  a=RankOfQueue=' ';
  for (;q<MELD_DEPTH;q++) Queue[q] = EMPTY;
  if (ForTake) n=1;
  for (q=0;q<MELD_DEPTH;q++) {
    a = ReadMenu(gMeldMenu,MELD_PULLDOWN_COUNT);
    if (a == 0x0D) break;
    if (a == 'x') break;
    a = toupper(a);
    b = SelectCardInHand(PLAYER,a);
    if (b == EMPTY) q--;
    else {
      for (i=1;i<=5;i++) {
        for (j=(22*(i-1));j<(22*i);j++) {
          if (j>=DECK_SIZE) break;
          if (gHand[PLAYER][j].Index != EMPTY) {
            if (gHand[PLAYER][j].Selected) {
              Gprintf( STATUS_LINE-(6-i), (((22*i)-j-1)*3)+15, YELLOW,
                BLACK, "%c",0xFE);
            }
          }
        }
      }
      c = gHand[PLAYER][b].Index;
      Queue[q] = c;
      if (gCard[c].IsWild) {
        w++;
      }
      else {
        n++;
        if (RankOfQueue == ' ') RankOfQueue = a;
        else {
          if (RankOfQueue != a) {
            DeselectAllInHand(PLAYER);
            return ' ';
          }
        }
      }
    }
  }
  if (RankOfQueue == ' ') {
    if (ForTake) return ' ';
    cleardevice();
    Gprintf(1,1,YELLOW,BLACK,
      "On which rank do you want those wilds to be placed?");
    a = ReadMenu(gNatualRankMenu,NATURAL_RANK_PULLDOWN_COUNT);
    RankOfQueue = toupper(a);
  }
  switch (RankOfQueue) {
  case '3': r= 0; break;
  case '4': r= 1; break;
  case '5': r= 2; break;
  case '6': r= 3; break;
  case '7': r= 4; break;
  case '8': r= 5; break;
  case '9': r= 6; break;
  case 'T': r= 7; break;
  case 'J': r= 8; break;
  case 'Q': r= 9; break;
  case 'K': r=10; break;
  case 'A': r=11; break;
  default:
    DeselectAllInHand(PLAYER);
    return ' ';
  }
  for(t=0;t<MELD_DEPTH;t++) {
    p = gMeld[PLAYER][r].Position[t];
    if (p == EMPTY) break;
    if (gCard[p].IsWild)
         w++;
    else n++;
  }
  if ((n+w)<3) {
    DeselectAllInHand(PLAYER);
    return ' ';
  }

  else {
    if (n<w) {
      DeselectAllInHand(PLAYER);
      return ' ';
    }
    else {
      if (ForTake) {
        gMeld[PLAYER][r].Position[t] = gDiscard[gTopPile];
        gDiscard[gTopPile] = EMPTY;
        gTopPile--; t++;
      }
      for (q=0;q<MELD_DEPTH;q++,t++) {
        if (Queue[q] == EMPTY) break;
        gMeld[PLAYER][r].Position[t] = Queue[q];
        for (b=0;b<DECK_SIZE;b++) {
          if (gHand[PLAYER][b].Index == Queue[q]) break;
        }
        gHand[PLAYER][b].Index = EMPTY;
        gHand[PLAYER][b].Rank = '~';
        gHand[PLAYER][b].Selected = false;
        gpHandCardCount--;
      }
      gpMeldedBefore = true;
      SortHand(PLAYER);
    }
  }
  DeselectAllInHand(PLAYER);

  return RankOfQueue;
}

/*

This function melds all the natural cards it can from the computer
hand.

*/

void far cMeldAllNaturals() {
  int  CardList[20];
  int  i, j, k;
  int  MeldPit;
  int  NatCount[11];
  char *ptr;
  char RankOfCardInList;
  int  DeckIndex;

  for (i=0; i<11; i++) NatCount[i]= 0;
  for (i=0; i<DECK_SIZE; i++) {
    DeckIndex = gHand[COMPUTER][i].Index;
    if ( DeckIndex == EMPTY ) break;
    RankOfCardInList = gCard[DeckIndex].Title[0];
    ptr = strchr( gRankString, RankOfCardInList );
    switch ( RankOfCardInList ) {
    case 'Z':
    case '2':
    case '3':
      break;
    default:
      NatCount[(int) (ptr-gRankString)-1]++;
    }
  }
  for (i=0; i<20; i++) CardList[i] = EMPTY;
  RankOfCardInList = ' ';
  for ( i=8; i>2; i--) {
    for ( j=10; j>=0; j-- ) {
      if ( NatCount[j] == i ) {
        RankOfCardInList = gRankString[j+1];
        NatCount[j] = 0;
        break;
      }
    }
    if ( RankOfCardInList != ' ' ) break;
  }
  if ( RankOfCardInList != ' ' ) {
    for (i=0, j=0; i<DECK_SIZE; i++) {
      DeckIndex = gHand[COMPUTER][i].Index;
      if ( DeckIndex == EMPTY ) break;
      if ( gCard[DeckIndex].Title[0] == RankOfCardInList )
        CardList[j++] = DeckIndex;
    }
    MeldPit = cFindMeldPit( RankOfCardInList );
    if ( MeldPit == EMPTY ) {
      switch (RankOfCardInList) {
      case '4': MeldPit =  1; break;
      case '5': MeldPit =  2; break;
      case '6': MeldPit =  3; break;
      case '7': MeldPit =  4; break;
      case '8': MeldPit =  5; break;
      case '9': MeldPit =  6; break;
      case 'T': MeldPit =  7; break;
      case 'J': MeldPit =  8; break;
      case 'Q': MeldPit =  9; break;
      case 'K': MeldPit = 10; break;
      case 'A': MeldPit = 11; break;
      }
    }
    for (i=0; i<MELD_DEPTH; i++) {
      DeckIndex = gMeld[COMPUTER][MeldPit].Position[i];
      if ( DeckIndex == EMPTY ) break;
    }
    for ( j=0; j<MELD_DEPTH; j++ ) {
      DeckIndex = CardList[j];
      if ( DeckIndex == EMPTY ) break;
      gMeld[COMPUTER][MeldPit].Position[i+j] = DeckIndex;
      for ( k=0; k<DECK_SIZE; k++ ) {
        DeckIndex = gHand[COMPUTER][k].Index;
        if ( DeckIndex == CardList[j] ) break;
      }
      gHand[COMPUTER][k].Index = EMPTY;
      gHand[COMPUTER][k].Rank = '~';
      gHand[COMPUTER][k].Selected = false;
      gcHandCardCount--;
    }
    SortHand(COMPUTER);
  }
}

/*

This function returns the value of the minimum legal first meld score
stepped at 15, 50, 90, and 120 for a score from the previous round of
less than 0, 1500, 3000, and greater than 3000 for the computer hand.

*/

int far cMinLegalMeld() {
  int MinMeld = 0;

  if (gRounds <= 1) {
    MinMeld = 50;
  }
  else {
    if (gScore[gRounds-2][COMPUTER] >= 3000) {
      MinMeld = 120;
    }
    else {
      if (gScore[gRounds-2][COMPUTER] >= 1500) {
        MinMeld = 90;
      }
      else {
        if (gScore[gRounds-2][COMPUTER] >= 0) {
          MinMeld = 50;
        }
        else {
          MinMeld = 15;
        }
      }
    }
  }
  return MinMeld;
}

/*

This function returns the value of the minimum legal first meld score
stepped at 15, 50, 90, and 120 for a score from the previous round of
less than 0, 1500, 3000, and greater than 3000 for the use hand.
Includes the top of the discard pile if for take. Returns all cards
back to the hand except red threes on fail.

*/

int far pCalcFirstMeld() {
  int Result = 0;

  if (gRounds <= 1) Result = 50;
  else {
    if (gScore[gRounds-2][PLAYER] >= 3000) Result = 120;
    else {
      if (gScore[gRounds-2][PLAYER] >= 1500) Result = 90;
      else {
        if (gScore[gRounds-2][PLAYER] >= 0) Result = 50;
        else Result = 15;
      }
    }
  }

  return Result;
}

bool far pMinLegalMeld(bool ForTake) {
  int l,d,c,CurrMeld,MinMeld;

  l=d=c=CurrMeld=MinMeld=0;
  MinMeld = pCalcFirstMeld();
  for (l=1;l<MELD_LOCATIONS;l++) {
    for (d=0;d<=MELD_DEPTH;d++) {
      c = gMeld[PLAYER][l].Position[d];
      if (c == EMPTY) break;
      CurrMeld += gCard[c].Value;
    }
  }
  if ((CurrMeld > 0 ) && (CurrMeld < MinMeld )) {
    if (ForTake) return false;
    cleardevice();
    Gprintf(1,1,YELLOW,BLACK,
      "All melds are being return to your hand.");
    Gprintf(2,1,YELLOW,BLACK,"Press a key to continue.");
    getch();
    gpMeldedBefore = false;
    for (c=0;c<DECK_SIZE;c++) {
      if (gHand[PLAYER][c].Index == EMPTY) break;
    }
    for (l=1;l<MELD_LOCATIONS;l++) {
      gMeld[PLAYER][l].IsBook = false;
      gMeld[PLAYER][l].HasWild = false;
      for (d=0;d<=MELD_DEPTH;d++) {
        if (gMeld[PLAYER][l].Position[d] == EMPTY) break;
        gHand[PLAYER][c].Index = gMeld[PLAYER][l].Position[d];
        gHand[PLAYER][c].Rank = gCard[gHand[PLAYER][c].Index].Rank;
        gMeld[PLAYER][l].Position[d] = EMPTY;
        gpHandCardCount++;
        c++;
      }
    }
    SortHand(PLAYER);
    return false;
  }
  return true;
}

/*

This function provides a variety of cardbacks.

*/

void far NextCardBack() {
  int a = gLastCB;

  while (a == gLastCB) a = rand() % 32;
  gLastCB = a;
  switch (a) {
  case  0: strcpy(gCardBackFileName, "CB0.PXL");   break;
  case  1: strcpy(gCardBackFileName, "CB1.PXL");   break;
  case  2: strcpy(gCardBackFileName, "CB2.PXL");   break;
  case  3: strcpy(gCardBackFileName, "CB3.PXL");   break;
  case  4: strcpy(gCardBackFileName, "CB4.PXL");   break;
  case  5: strcpy(gCardBackFileName, "CB5.PXL");   break;
  case  6: strcpy(gCardBackFileName, "CB6.PXL");   break;
  case  7: strcpy(gCardBackFileName, "CB7.PXL");   break;
  case  8: strcpy(gCardBackFileName, "CB8.PXL");   break;
  case  9: strcpy(gCardBackFileName, "CB9.PXL");   break;
  case 10: strcpy(gCardBackFileName, "CBA.PXL");   break;
  case 11: strcpy(gCardBackFileName, "CBB.PXL");   break;
  case 12: strcpy(gCardBackFileName, "CBC.PXL");   break;
  case 13: strcpy(gCardBackFileName, "CBD.PXL");   break;
  case 14: strcpy(gCardBackFileName, "CBE.PXL");   break;
  case 15: strcpy(gCardBackFileName, "CBF.PXL");   break;
  case 16: strcpy(gCardBackFileName, "BYC_0.PXL"); break;
  case 17: strcpy(gCardBackFileName, "BYC_1.PXL"); break;
  case 18: strcpy(gCardBackFileName, "BYC_2.PXL"); break;
  case 19: strcpy(gCardBackFileName, "BYC_3.PXL"); break;
  case 20: strcpy(gCardBackFileName, "BYC_4.PXL"); break;
  case 21: strcpy(gCardBackFileName, "BYC_5.PXL"); break;
  case 22: strcpy(gCardBackFileName, "BYC_6.PXL"); break;
  case 23: strcpy(gCardBackFileName, "BYC_7.PXL"); break;
  case 24: strcpy(gCardBackFileName, "BYC_8.PXL"); break;
  case 25: strcpy(gCardBackFileName, "BYC_9.PXL"); break;
  case 26: strcpy(gCardBackFileName, "BYC_A.PXL"); break;
  case 27: strcpy(gCardBackFileName, "BYC_B.PXL"); break;
  case 28: strcpy(gCardBackFileName, "BYC_C.PXL"); break;
  case 29: strcpy(gCardBackFileName, "BYC_D.PXL"); break;
  case 30: strcpy(gCardBackFileName, "BYC_E.PXL"); break;
  case 31: strcpy(gCardBackFileName, "BYC_F.PXL"); break;
  }
}

/*

This function checks for capability of computer hand to "go out".

*/

void far cOutCapabile() {
  int  Pos1, Pos2;
  int  i, j, o01K;
  int  Singletons = 0;
  int  Doubletons = 0;
  int  NatCount[12];
  int  MeldPit;
  int  WldCount = 0;
  char *ptr;
  char Rank, OldRank;
  bool Pass = true;

// 14Jul2011 Changed condition from < 1 to < NUMBER_CANASTA_OUT
  if ( gcCanastaCount < NUMBER_CANASTA_OUT ) return;
  for (i=0; i<12; i++) NatCount[i]= 0;
  for (i=0; i<DECK_SIZE; i++) {
    Pos1 = gHand[COMPUTER][i].Index;
    if ( Pos1 == EMPTY ) break;
    Rank = gCard[Pos1].Title[0];
    ptr = strchr( gRankString, Rank );
    switch ( Rank ) {
    case '2':
    case 'Z':
      WldCount++;
      break;
    default:
      NatCount[(int) (ptr-gRankString)]++;
    }
  }
  for (i=0; i<12; i++) {
    switch ( NatCount[i] ) {
    case 1:
      if ( ++Singletons > 1 ) Pass = false;
      break;
    case 2:
      if ( ++Doubletons > WldCount ) Pass = false;
    }
    if ( Pass == false ) break;
  }
  if ( Doubletons != WldCount ) Pass = false;
  if ( Pass ) {
    Singletons = 0;
    OldRank = ' ';
    for (i=0; i<DECK_SIZE; i++) {
      Pos1 = gHand[COMPUTER][i].Index;
      if ( Pos1 == EMPTY ) break;
      Rank = gCard[Pos1].Title[0];
      if ( OldRank == ' ' ) {
        Singletons++;
        MeldPit = EMPTY;
        MeldPit = cFindMeldPit( Rank );
        if ( MeldPit == EMPTY ) {
          switch (Rank) {
          case '3': MeldPit =  0; break;
          case '4': MeldPit =  1; break;
          case '5': MeldPit =  2; break;
          case '6': MeldPit =  3; break;
          case '7': MeldPit =  4; break;
          case '8': MeldPit =  5; break;
          case '9': MeldPit =  6; break;
          case 'T': MeldPit =  7; break;
          case 'J': MeldPit =  8; break;
          case 'Q': MeldPit =  9; break;
          case 'K': MeldPit = 10; break;
          case 'A': MeldPit = 11; break;
          }
        }
        for ( j=0; j<MELD_DEPTH; i++) {
          Pos2 = gMeld[COMPUTER][MeldPit].Position[j];
          if ( Pos2 == EMPTY ) break;
        }
        gMeld[COMPUTER][MeldPit].Position[j] = Pos1;
        gHand[COMPUTER][i].Index = EMPTY;
        gHand[COMPUTER][i].Rank = '~';
        gHand[COMPUTER][i].Selected = false;
        gcHandCardCount--;
      }
      else {
        if ( Rank == OldRank ) {
          Singletons++;
          gMeld[COMPUTER][MeldPit].Position[j] = Pos1;
          gHand[COMPUTER][i].Index = EMPTY;
          gHand[COMPUTER][i].Rank = '~';
          gHand[COMPUTER][i].Selected = false;
          gcHandCardCount--;
        }
        else {
          if ( Singletons == 2 ) {
            for ( o01K=0; o01K<DECK_SIZE; o01K++ ) {
              Pos2 = gHand[COMPUTER][o01K].Index;
              if ((gCard[Pos2].Title[0] == 'Z') ||
                  (gCard[Pos2].Title[0] == '2')) {
                gMeld[COMPUTER][MeldPit].Position[j] = Pos2;
                gHand[COMPUTER][o01K].Index = EMPTY;
                gHand[COMPUTER][o01K].Rank = '~';
                gHand[COMPUTER][o01K].Selected = false;
                gcHandCardCount--;
                break;
              }
            }
          }
          Singletons = 1;
          MeldPit = EMPTY;
          MeldPit = cFindMeldPit( Rank );
          if ( MeldPit == EMPTY ) {
            switch (Rank) {
            case '3': MeldPit =  0; break;
            case '4': MeldPit =  1; break;
            case '5': MeldPit =  2; break;
            case '6': MeldPit =  3; break;
            case '7': MeldPit =  4; break;
            case '8': MeldPit =  5; break;
            case '9': MeldPit =  6; break;
            case 'T': MeldPit =  7; break;
            case 'J': MeldPit =  8; break;
            case 'Q': MeldPit =  9; break;
            case 'K': MeldPit = 10; break;
            case 'A': MeldPit = 11; break;
            }
          }
          for ( j=0; j<MELD_DEPTH; i++) {
            Pos2 = gMeld[COMPUTER][MeldPit].Position[j];
            if ( Pos2 == EMPTY ) break;
          }
          gMeld[COMPUTER][MeldPit].Position[j] = Pos1;
          gHand[COMPUTER][i].Index = EMPTY;
          gHand[COMPUTER][i].Rank = '~';
          gHand[COMPUTER][i].Selected = false;
          gcHandCardCount--;
        }
      }
      OldRank = Rank;
    }
    SortHand(COMPUTER);
  }

  return;
}

/*

This function enables the mouse environment while waiting for user
input.

*/

char far ReadDesktop() {
  char KeyStroke[3] = "";
  bool Continuing=true;
#ifdef USE_MOUSE
  int i=0;
  int SaveX=gMouseInformation.x;
  int SaveY=gMouseInformation.y;

  MouseOn( &gMouseInformation );
#endif
  while ( Continuing ) {
    KeyStroke[0] = KeyStroke[1] = KeyStroke[2] = 0x00;
#ifdef USE_MOUSE
    while ( kbhit() ) getch();
    while ( !kbhit()
      && !MouseHit( &gMouseInformation )
      ) {
      if ((SaveX!=gMouseInformation.x)||(SaveY!=gMouseInformation.y)) {
        Gprintf( STATUS_LINE, 75, STATUS_FOR, STATUS_BACK, "%2d,%2d",
          gMouseInformation.y-1, gMouseInformation.x-1 );
      }
      SaveX = gMouseInformation.x;
      SaveY = gMouseInformation.y;
    }
#endif
    if ( kbhit() ) {
      KeyStroke[0] = getch();
      if ( KeyStroke[0] == 0x00 ) {
        KeyStroke[1] = getch();
        switch (KeyStroke[1]) {
        case 34: KeyStroke[0] = 'x'; break;
        case 24: KeyStroke[0] = 'y'; break;
        case 35: KeyStroke[0] = 'z';
        }
      }
#ifdef USE_MOUSE
      MouseOff( &gMouseInformation ); MouseOn( &gMouseInformation );
#endif
      Continuing = false;
    }
#ifdef USE_MOUSE
    if ( MouseHit( &gMouseInformation ) ) {
      MouseGet( &gMouseInformation );
      switch ( gMouseInformation.Button ) {
      case 1:
        for ( i=0; i<DESKTOP_BUTTON_COUNT; i++ ) {
          if (( gMouseInformation.y-1 >= gDesktop[gPhase][i].row1 ) &&
              ( gMouseInformation.y-1 <= gDesktop[gPhase][i].row2 ) &&
              ( gMouseInformation.x-1 >= gDesktop[gPhase][i].col1 ) &&
              ( gMouseInformation.x-1 <= gDesktop[gPhase][i].col2 ) ) {
            KeyStroke[0] = gDesktop[gPhase][i].letter;
            Continuing = false;
            break;
          }
        }
        if (Continuing) {
          KeyStroke[0] = 0x00;
          Continuing = false;
        }
        break;
      case 2:
        KeyStroke[0] = 0x1B;
        Continuing = false;
      }
    }
#endif
    // Otherwize continue
  }
#ifdef USE_MOUSE
  MouseOff( &gMouseInformation );
#endif
  if ( KeyStroke[0] ) {
    if ((KeyStroke[0] >= 'A') && (KeyStroke[0] <= 'Z')) {
      // lowercase
      KeyStroke[0] += ' ';
    }
  }

  return KeyStroke[0];
}

/*

This largely redundant function repeats the one above, but with respect
to a pull-down menu. The desktop is disabled while in this function.

*/

char far ReadMenu(cMenu *PullDown, int Entries) {
  char KeyStroke[3];
  bool Continuing=true;

  ShowMenu(PullDown,Entries);
#ifdef USE_MOUSE
  int i=0;
  MouseOn( &gMouseInformation );
#endif
  while ( Continuing ) {
    KeyStroke[0] = KeyStroke[1] = KeyStroke[2] = NULL;
#ifdef USE_MOUSE
    while ( kbhit() ) getch();
    while ( !kbhit() && !MouseHit( &gMouseInformation ) );
#endif
    if ( kbhit() ) {
      KeyStroke[0] = getch();
      if ( KeyStroke[0] == NULL ) KeyStroke[1] = getch();
#ifdef USE_MOUSE
      MouseOff( &gMouseInformation ); MouseOn( &gMouseInformation );
#endif
      Continuing = false;
    }
#ifdef USE_MOUSE
    if ( MouseHit( &gMouseInformation ) ) {
      MouseGet( &gMouseInformation );
      switch ( gMouseInformation.Button ) {
      case 1:
        for ( i=0; i<Entries; i++ ) {
          if (( gMouseInformation.y-1 >= PullDown[i].row1 ) &&
              ( gMouseInformation.y-1 <= PullDown[i].row2 ) &&
              ( gMouseInformation.x-1 >= PullDown[i].col1 ) &&
              ( gMouseInformation.x-1 <= PullDown[i].col2 ) ) {
            KeyStroke[0] = PullDown[i].letter;
            Continuing = false;
            break;
          }
        }
        if (Continuing) {
          KeyStroke[0] = 0x00;
          Continuing = false;
        }
        break;
      case 2:
        KeyStroke[0] = 0x1B;
        Continuing = false;
      }
    }
#endif
    // Otherwize continue
  }
#ifdef USE_MOUSE
  MouseOff( &gMouseInformation );
#endif
  if ( KeyStroke[0] ) {
    if ((KeyStroke[0] >= 'A') && (KeyStroke[0] <= 'Z')) {
      // lowercase
      KeyStroke[0] += ' ';
    }
  }
  HideMenu(PullDown,Entries);

  return KeyStroke[0];
}

/*

This function refreshes the screen from top to bottom.

*/

void far Refresh() {
  int i,j,a,n;

  i=j=a=n=0;
  cleardevice();

  /*

  Special case: Search for red threes in both hands to correct for
  taking pile with a red three at bottom from begining of round.

  */
  gcHandCardCount = 0;
  for (i=DECK_SIZE-1;i>=0;i--) {
    n = gHand[COMPUTER][i].Index;
    if (n != EMPTY) {
      gcHandCardCount++;
      if (IsRedThree(COMPUTER,n)) {
        gHand[COMPUTER][i].Index = EMPTY;
        gHand[COMPUTER][i].Rank = '~';
        gHand[COMPUTER][i].Selected = false;
        gcHandCardCount--;
        SortHand(COMPUTER);
      }
    }
  }
  gpHandCardCount = 0;
  for (i=DECK_SIZE-1;i>=0;i--) {
    n = gHand[PLAYER][i].Index;
    if (n != EMPTY) {
      gpHandCardCount++;
      if (IsRedThree(PLAYER,n)) {
        gHand[PLAYER][i].Index = EMPTY;
        gHand[PLAYER][i].Rank = '~';
        gHand[PLAYER][i].Selected = false;
        gpHandCardCount--;
        SortHand(PLAYER);
      }
    }
  }

  /*

  Computer Hand gHand0 -- only the bottom row card backs in two rows
  for 108 cards

  */

  for (i=DECK_SIZE-1;i>=54;i--) {
    n = gHand[COMPUTER][i].Index;
    if (n != EMPTY) {
      GetPixelsFromFile( gCardBackFileName, -7, (107-i)+18, false );
    }
  }
  for (i=53;i>=0;i--) {
    if (gHand[COMPUTER][i].Index != EMPTY) {
#ifdef TESTING
// Face up display of hand
      DisplayCard(gHand[COMPUTER][i].Index, -8, i*2, false);
#else
      GetPixelsFromFile( gCardBackFileName, -9, (53-i)+18, false );
#endif
    }
  }

  // Computer Melds -- all threes as Meld0

  ShowMelds(COMPUTER,5);

  // Score Pad -- showing written bonus and melds

  ShowScore();

  // Stock -- with number of cards left

  Gprintf(STOCK_ROW-1,STOCK_COLUMN+3,YELLOW,BLACK,"%3d",
    gNextCardInStock+1);
  if (gNextCardInStock >= 0) {
    GetPixelsFromFile( "DECKSIDE.PXL",    STOCK_ROW, STOCK_COLUMN-1,
      false );
    GetPixelsFromFile( gCardBackFileName, STOCK_ROW, STOCK_COLUMN,
      false );
  }

  // Discard Pile -- with wilds and red threes sideways

  if (gTopPile <= EMPTY) gTopPile = EMPTY; // bug fix
  for (i=0;i<DECK_SIZE;i++) {
    a = gDiscard[i];
    if (a == EMPTY) break;
    else {
      if (gCard[a].IsWild) {
        DisplayCard(a,STOCK_ROW,STOCK_COLUMN+9,true);
      }
      else {
        if ((gCard[a].Title[0] == '3') &&
           ((gCard[a].Title[1] == 'H') ||
            (gCard[a].Title[1] == 'D'))) {
          DisplayCard(a,STOCK_ROW,STOCK_COLUMN+9,true);
        }
        else DisplayCard(a,STOCK_ROW,STOCK_COLUMN+9,false);
      }
    }
  }
  Gprintf(STOCK_ROW-1,STOCK_COLUMN+10,YELLOW,BLACK,"%3d",
    gTopPile+1);

  // Player Melds -- all threes as Meld0

  ShowMelds(PLAYER,37);

  /*

  Player Hand -- five rows for 108 cards, last row is hardly ever
  used. The cards have a small designation in the upper right corner.

  */

  for (i=1;i<=5;i++) {
    for (j=(22*(i-1));j<(22*i);j++) {
      if (j>=DECK_SIZE) break;
      if (gHand[PLAYER][j].Index != EMPTY) {
        DisplayCard(gHand[PLAYER][j].Index, STATUS_LINE-(6-i),
          (((22*i)-j-1)*3)+7, false);
      }
    }
  }

  // Status Line -- showing all currents

  Gprintf(STATUS_LINE, 0,STATUS_FOR,STATUS_BACK, "%80.80s"," " );
  if (gpMeldedBefore) {
    Gprintf(STATUS_LINE, 0,STATUS_FOR,STATUS_BACK,
      " Round %d |", gRounds );
  } else {
    Gprintf(STATUS_LINE, 0,STATUS_FOR,STATUS_BACK,
      " Round %d | first meld = %d |", gRounds, (pCalcFirstMeld()) );
  }
  Gprintf(STATUS_LINE,50,STATUS_FOR,STATUS_BACK, "%s (%s)", PROGNAME,
    VERSION );

  // Desktop Menu Bar

  Gprintf( 0, 0, BLACK, WHITE, "%80.80s"," " );
  for (i=0;i<DESKTOP_BUTTON_COUNT;i++) {
    Gprintf(gDesktop[gPhase][i].row1,gDesktop[gPhase][i].col1,BLACK,
      WHITE, "%s", gDesktop[gPhase][i].caption );
    Gprintf(gDesktop[gPhase][i].row1,gDesktop[gPhase][i].col1+1,RED,
      WHITE, "%c", gDesktop[gPhase][i].caption[1] );
  }

  // Check if Player or Computer is out, or if the Stock is empty.

  if (gpHandCardCount <= 0)      gEndRound = true;
  if (gcHandCardCount <= 0)      gEndRound = true;
  if (gNextCardInStock == EMPTY) gEndRound = true;
}

/*

This function restores pixels behind a pull-down menu from a file.

*/

void far RestoreBehindWindow(char *FileName, int Top, int Left,
       int Bottom, int Right) {
  int i, j;
  int PixelTop = Top*gTextHeight;
  int PixelLeft = Left*gTextWidth;
  int PixelBottom = ((Bottom+1)*gTextHeight)-1;
  int PixelRight = ((Right+1)*gTextWidth)-1;
  FILE *InFile;
  char InChar = ' ';

  i=j=0;
  if ( (InFile = fopen(FileName, "rb")) == NULL ) {
    ProgramDestructor();
    printf("Error in %s: Cannot open %s file.\n", PROGNAME, FileName);
    exit( 2 );
  }

  for (i=PixelTop;i<=PixelBottom;i++) {
    for (j=PixelLeft;j<=PixelRight;j++) {
      InChar = fgetc( InFile );
      switch (InChar) {
      case '0': putpixel(j,i, 0); break;
      case '1': putpixel(j,i, 1); break;
      case '2': putpixel(j,i, 2); break;
      case '3': putpixel(j,i, 3); break;
      case '4': putpixel(j,i, 4); break;
      case '5': putpixel(j,i, 5); break;
      case '6': putpixel(j,i, 6); break;
      case '7': putpixel(j,i, 7); break;
      case '8': putpixel(j,i, 8); break;
      case '9': putpixel(j,i, 9); break;
      case 'A': putpixel(j,i,10); break;
      case 'B': putpixel(j,i,11); break;
      case 'C': putpixel(j,i,12); break;
      case 'D': putpixel(j,i,13); break;
      case 'E': putpixel(j,i,14); break;
      default : putpixel(j,i,15);
      }
    }
  }
  fclose(InFile);
}

/*

This function restores the state of the computer to file.

*/

void far RestoreStateOfComputer() {
  FILE *InFile;
  int i,j,k;

  InFile = fopen("SAVESTAT.DTA","rb");

// Card Deck

  for (i=0;i<DECK_SIZE;i++) {
    fgets(gS,80,InFile);
    gCard[i].Shuffle[0] = gS[0];
    gCard[i].Shuffle[1] = gS[1];
    gCard[i].Shuffle[2] = gS[2];
    gCard[i].Shuffle[3] = gS[3];
    gCard[i].Title[0] = gS[4];
    gCard[i].Title[1] = gS[5];
    gCard[i].Title[2] = gS[6];
    gCard[i].Rank = gS[7];
    gCard[i].Suit = gS[8];
    gS[0] = gS[9];
    gS[1] = gS[10];
    gS[2] = gS[11];
    gS[3] = 0x00;
    gCard[i].Value = atoi(gS);
    if (gS[12] == 'T')
         gCard[i].IsWild = true;
    else gCard[i].IsWild = false;
  }

// Hands

  gpHandCardCount = 0;
  gcHandCardCount = 0;
  for (i=0;i<NUM_PLAYERS;i++) {
    for (j=0;j<DECK_SIZE;j++) {
      fgets(gS,80,InFile);
      gHand[i][j].Rank = gS[0];
      gS[0] = gS[1];
      gS[1] = gS[2];
      gS[2] = gS[3];
      gS[3] = 0x00;
      gHand[i][j].Index = atoi(gS);
      if (gS[4] == 'T')
           gHand[i][j].Selected = true;
      else gHand[i][j].Selected = false;
      if (i == PLAYER) gpHandCardCount++;
      if (i == COMPUTER) gcHandCardCount++;
    }
  }

// Top Discard Pile

  fgets(gS,80,InFile);
  gS[3] = 0x00;
  gTopPile = atoi(gS);

// Stock

  for (i=0;i<DECK_SIZE;i++) {
    fgets(gS,80,InFile);
    gS[3] = 0x00;
    gStock[i] = atoi(gS);
  }

// Discard Pile

  for (i=0;i<DECK_SIZE;i++) {
    fgets(gS,80,InFile);
    gS[3] = 0x00;
    gDiscard[i] = atoi(gS);
  }

// Melds and Red Trey

  for (i=0;i<NUM_PLAYERS;i++) {
    for (j=0;j<MELD_LOCATIONS;j++) {
      fgets(gS,80,InFile);
      if (gS[0] == 'T')
           gMeld[i][j].IsBook = true;
      else gMeld[i][j].IsBook = false;
      if (gS[1] == 'T')
           gMeld[i][j].HasWild = true;
      else gMeld[i][j].HasWild = false;
      for (k=0;k<MELD_DEPTH;k++) {
        gS[0] = gS[(k*3)+2];
        gS[1] = gS[(k*3)+3];
        gS[2] = gS[(k*3)+4];
        gS[3] = 0x00;
        gMeld[i][j].Position[k] = atoi(gS);
      }
    }
  }

// Score

  for (i=0;i<MAX_ROUNDS;i++) {
    fgets(gS,80,InFile);
    gS[60] = gS[5];
    gS[61] = gS[6];
    gS[62] = gS[7];
    gS[63] = gS[8];
    gS[64] = gS[9];
    gS[5] = 0x00;
    gBonusPoints[i][0] = atoi(gS);
    gS[0] = gS[60];
    gS[1] = gS[61];
    gS[2] = gS[62];
    gS[3] = gS[63];
    gS[4] = gS[64];
    gS[5] = 0x00;
    gBonusPoints[i][1] = atoi(gS);
    fgets(gS,80,InFile);
    gS[60] = gS[5];
    gS[61] = gS[6];
    gS[62] = gS[7];
    gS[63] = gS[8];
    gS[64] = gS[9];
    gS[5] = 0x00;
    gMeldPoints[i][0] = atoi(gS);
    gS[0] = gS[60];
    gS[1] = gS[61];
    gS[2] = gS[62];
    gS[3] = gS[63];
    gS[4] = gS[64];
    gS[5] = 0x00;
    gMeldPoints[i][1] = atoi(gS);
    fgets(gS,80,InFile);
    gS[60] = gS[5];
    gS[61] = gS[6];
    gS[62] = gS[7];
    gS[63] = gS[8];
    gS[64] = gS[9];
    gS[5] = 0x00;
    gScore[i][0] = atoi(gS);
    gS[0] = gS[60];
    gS[1] = gS[61];
    gS[2] = gS[62];
    gS[3] = gS[63];
    gS[4] = gS[64];
    gS[5] = 0x00;
    gScore[i][1] = atoi(gS);
  }

// Miscellaneous

  fgets(gS,80,InFile);
  if (gS[0] == 'T')
       gcMeldedBefore = true;
  else gcMeldedBefore = false;
  if (gS[1] == 'T')
       gpMeldedBefore = true;
  else gpMeldedBefore = false;
  gS[0] = gS[2];
  gS[1] = gS[3];
  gS[2] = gS[4];
  gS[3] = 0x00;
  gNextCardInStock = atoi(gS);
  gS[0] = gS[5];
  gS[1] = gS[6];
  gS[2] = gS[7];
  gS[3] = 0x00;
  gRounds = atoi(gS);
  fclose(InFile);
  Refresh();
}

/*

This function saves the state of the computer to file.

*/

void far SaveStateOfComputer() {
  FILE *OutFile;
  int i,j,k;

  OutFile = fopen("SAVESTAT.DTA","wb");

// Card Deck

  for (i=0;i<DECK_SIZE;i++) {
    fprintf(OutFile,"%c",gCard[i].Shuffle[0]);
    fprintf(OutFile,"%c",gCard[i].Shuffle[1]);
    fprintf(OutFile,"%c",gCard[i].Shuffle[2]);
    fprintf(OutFile,"%c",gCard[i].Shuffle[3]);
    fprintf(OutFile,"%c",gCard[i].Title[0]);
    fprintf(OutFile,"%c",gCard[i].Title[1]);
    fprintf(OutFile,"%c",gCard[i].Title[2]);
    fprintf(OutFile,"%c",gCard[i].Rank);
    fprintf(OutFile,"%c",gCard[i].Suit);
    fprintf(OutFile,"%3.1d",gCard[i].Value);
    if (gCard[i].IsWild)
         fprintf(OutFile,"T\r\n");
    else fprintf(OutFile,"F\r\n");
  }

// Hands

  for (i=0;i<NUM_PLAYERS;i++) {
    for (j=0;j<DECK_SIZE;j++) {
      fprintf(OutFile,"%c",gHand[i][j].Rank);
      fprintf(OutFile,"%3.1d",gHand[i][j].Index);
      if (gHand[i][j].Selected)
           fprintf(OutFile,"T\r\n");
      else fprintf(OutFile,"F\r\n");
    }
  }

// Top Discard Pile

  fprintf(OutFile,"%3.1d\r\n",gTopPile);

// Stock

  for (i=0;i<DECK_SIZE;i++)
    fprintf(OutFile,"%3.1d\r\n",gStock[i]);

// Discard Pile

  for (i=0;i<DECK_SIZE;i++)
    fprintf(OutFile,"%3.1d\r\n",gDiscard[i]);

// Melds and Red Trey

  for (i=0;i<NUM_PLAYERS;i++) {
    for (j=0;j<MELD_LOCATIONS;j++) {
      if (gMeld[i][j].IsBook)
           fprintf(OutFile,"T");
      else fprintf(OutFile,"F");
      if (gMeld[i][j].HasWild)
           fprintf(OutFile,"T");
      else fprintf(OutFile,"F");
      for (k=0;k<MELD_DEPTH;k++)
        fprintf(OutFile,"%3.1d",gMeld[i][j].Position[k]);
      fprintf(OutFile,"\r\n");
    }
  }

// Score

  for (i=0;i<MAX_ROUNDS;i++) {
    for (j=0;j<NUM_PLAYERS;j++) {
      fprintf(OutFile,"%5.1d",gBonusPoints[i][j]);
    }
    fprintf(OutFile,"\r\n");
    for (j=0;j<NUM_PLAYERS;j++) {
      fprintf(OutFile,"%5.1d",gMeldPoints[i][j]);
    }
    fprintf(OutFile,"\r\n");
    for (j=0;j<NUM_PLAYERS;j++) {
      fprintf(OutFile,"%5.1d",gScore[i][j]);
    }
    fprintf(OutFile,"\r\n");
  }

// Miscellaneous

  if (gcMeldedBefore)
       fprintf(OutFile,"T");
  else fprintf(OutFile,"F");
  if (gpMeldedBefore)
       fprintf(OutFile,"T");
  else fprintf(OutFile,"F");
  fprintf(OutFile,"%3.1d",gNextCardInStock);
  fprintf(OutFile,"%3.1d\r\n",gRounds);
  fclose(OutFile);
}

/*

This function saves pixels behind a pull-down menu into a file.

*/

void far SaveBehindWindow(char *FileName, int Top, int Left,
          int Bottom, int Right) {
  int i, j, ColorBuffer;
  int PixelTop = Top*gTextHeight;
  int PixelLeft = Left*gTextWidth;
  int PixelBottom = ((Bottom+1)*gTextHeight)-1;
  int PixelRight = ((Right+1)*gTextWidth)-1;
  FILE *OutFile;
  char OutChar=' ';

  i=j=ColorBuffer=0;
  OutFile = fopen(FileName, "wb");
  for (i=PixelTop;i<=PixelBottom;i++) {
    for (j=PixelLeft;j<=PixelRight;j++) {
      ColorBuffer = getpixel(j,i);
      switch (ColorBuffer) {
      case  0: OutChar = '0'; break;
      case  1: OutChar = '1'; break;
      case  2: OutChar = '2'; break;
      case  3: OutChar = '3'; break;
      case  4: OutChar = '4'; break;
      case  5: OutChar = '5'; break;
      case  6: OutChar = '6'; break;
      case  7: OutChar = '7'; break;
      case  8: OutChar = '8'; break;
      case  9: OutChar = '9'; break;
      case 10: OutChar = 'A'; break;
      case 11: OutChar = 'B'; break;
      case 12: OutChar = 'C'; break;
      case 13: OutChar = 'D'; break;
      case 14: OutChar = 'E'; break;
      default: OutChar = 'F';
      }
      fputc( OutChar, OutFile );
    }
  }
  fclose(OutFile);
}

/*

This function returns EMPTY or index in hand for selected occurance.

*/

int far SelectCardInHand(int Who, char a) {
  int i,b;

  i=b=0;
  for (;i<DECK_SIZE;i++) {
    b = gHand[Who][i].Index;
    if (b != EMPTY) {
      if (gCard[b].Title[0] == a) {
        if (!(gHand[Who][i].Selected)) {
          gHand[Who][i].Selected = true;
          return i;
        }
      }
    }
  }

  return EMPTY;
}

/*

This function involves the complicated procedure of displaying the
melds of a given side.

*/

void far ShowMelds(int Who, int Row) {
  int i,j,a;

  i=j=a=0;
  if (Who == COMPUTER) gcCanastaCount = 0;
  if (Who == PLAYER) gpCanastaCount = 0;
  for (i=0;i<MELD_LOCATIONS;i++) {
    gMeld[Who][i].IsBook = false;
    gMeld[Who][i].HasWild = false;
    for (j=0;j<MELD_DEPTH;j++) {
      a = gMeld[Who][i].Position[j];
      if (a == EMPTY) break;
      if (gCard[a].IsWild) gMeld[Who][i].HasWild = true;
    }
    if (j>=7) gMeld[Who][i].IsBook = true;
  }
  for (i=MELD_LOCATIONS-1;i>=1;i--) {
    if (gMeld[Who][i].IsBook) {
      if (gMeld[Who][i].HasWild) {

// Black canasta

        for (j=0;j<MELD_DEPTH;j++) {
          a = gMeld[Who][i].Position[j];
          if (gCard[a].IsWild) {
            DisplayCard(a,Row+4,i*6, false);
            break;
          }
        }
        for (j=0;j<MELD_DEPTH;j++) {
          a = gMeld[Who][i].Position[j];
          if (!(gCard[a].IsWild)) {
            DisplayCard(a,Row+5,i*6, false);
            break;
          }
        }
      }
      else {

// Red canasta

        for (j=0;j<MELD_DEPTH;j++) {
          a = gMeld[Who][i].Position[j];
          if (!(gCard[a].IsWild)) {
            if ((gCard[a].Suit == 'H') || (gCard[a].Suit == 'D')) {
              DisplayCard(a,Row+5,i*6, false);
              break;
            }
          }
        }
      }
      GetPixelsFromFile("DECKSIDE.PXL",Row+5,(i*6)-1, false );
      if (Who == COMPUTER) gcCanastaCount++;
      if (Who == PLAYER) gpCanastaCount++;
    }
    else {

// Non-canasta

      for (j=0;j<6;j++) {
        if (gMeld[Who][i].Position[j] == EMPTY) break;
        DisplayCard(gMeld[Who][i].Position[j], j+Row, i*6, false );
      }
    }
  }
  for (j=0;j<8;j++) {

// Threes

    if (gMeld[Who][0].Position[j] != EMPTY) {
      DisplayCard(gMeld[Who][0].Position[j], j+Row, 0, false );
    }
  }
}

/*

This function displays a specified menu with specified number of
entries.

*/

void far ShowMenu(cMenu *PullDown, int Entries) {
  int i=0;
  int MenuWidth = strlen(PullDown[0].caption);
  int Top = PullDown[0].row1-1;
  int Left = PullDown[0].col1-1;
  int Bottom  = PullDown[Entries-1].row1+1;
  int Right  = PullDown[Entries-1].col1+MenuWidth;

  SaveBehindWindow("MENUBACK.DTA", Top, Left, Bottom +1, Right +1);
  Gprintf(Top, Left, BLACK, WHITE, "Ú");
  for (i=0;i<MenuWidth;i++ )
    Gprintf(Top, PullDown[0].col1+i, BLACK, WHITE, "Ä");
  Gprintf(Top, PullDown[0].col1+MenuWidth, BLACK, WHITE, "¿");
  for (i=0;i<Entries;i++) {
    Gprintf(PullDown[i].row1, PullDown[i].col1-1, BLACK, WHITE, "³");
    Gprintf(PullDown[i].row1, PullDown[i].col1, BLACK, WHITE,
      "%*.*s", MenuWidth, MenuWidth, PullDown[i].caption);
    Gprintf(PullDown[i].row1, PullDown[i].col1+MenuWidth,
      BLACK, WHITE, "³%c",0xB2);
    Gprintf(PullDown[i].row1, PullDown[i].col1+1,
      RED, WHITE, "%c", PullDown[i].caption[1]);
  }
  Gprintf(Bottom , Left, BLACK, WHITE, "À");
  for (i=1;i<=MenuWidth;i++ )
    Gprintf(Bottom , Left+i, BLACK, WHITE, "Ä");
  Gprintf(Bottom , Right, BLACK, WHITE, "Ù%c",0xB2);
  for (i=1;i<=MenuWidth+2;i++ )
    Gprintf(Bottom +1, Left+i, BLACK, WHITE, "%c",0xB2);
}

/*

This function displays the running table of scores.

*/

void far ShowScore() {
  int i;

  if (gRounds<=1) return;
  Gprintf(STOCK_ROW-1, 1,YELLOW,BLACK,"    Player | Computer");
  for (i=1;i<gRounds;i++) {
    if (gScore[i-1][PLAYER] == 0) break;
    Gprintf(STOCK_ROW+(i*4)-4, 1,YELLOW,BLACK,"B:");
    Gprintf(STOCK_ROW+(i*4)-4, 3,YELLOW,BLACK,"%9.1d",
      gBonusPoints[i-1][PLAYER]);
    Gprintf(STOCK_ROW+(i*4)-4,12,YELLOW,BLACK,"|%9.1d",
      gBonusPoints[i-1][COMPUTER]);
    Gprintf(STOCK_ROW+(i*4)-3, 1,YELLOW,BLACK,"M:");
    Gprintf(STOCK_ROW+(i*4)-3, 3,YELLOW,BLACK,"%9.1d",
      gMeldPoints[i-1][PLAYER]);
    Gprintf(STOCK_ROW+(i*4)-3,12,YELLOW,BLACK,"|%9.1d",
      gMeldPoints[i-1][COMPUTER]);
    Gprintf(STOCK_ROW+(i*4)-2, 1,YELLOW,BLACK,"  ---------|---------");
    Gprintf(STOCK_ROW+(i*4)-1, 1,YELLOW,BLACK,"T:");
    Gprintf(STOCK_ROW+(i*4)-1, 3,YELLOW,BLACK,"%9.1d",
      gScore[i-1][PLAYER]);
    Gprintf(STOCK_ROW+(i*4)-1,12,YELLOW,BLACK,"|%9.1d",
      gScore[i-1][COMPUTER]);
  }
}

/*

This function shuffles the deck.

*/

void far ShuffleDeck() {
  int i;

  for (i=0;i<DECK_SIZE;i++) {
    sprintf(gRecord[i]  ,"%3.3s",gCard[i].Shuffle);
    sprintf(gRecord[i]+3,"%2.2s",gCard[i].Title);
    sprintf(gRecord[i]+5,"%c",gCard[i].Rank);
    sprintf(gRecord[i]+6,"%c",gCard[i].Suit);
    sprintf(gRecord[i]+7,"%2d",gCard[i].Value);
    if (gCard[i].IsWild)
         sprintf(gRecord[i]+9,"T");
    else sprintf(gRecord[i]+9,"F");
    gRecord[i][10] = 0x00;
  }

  qsort((void *)gRecord, DECK_SIZE, sizeof(gRecord[0]), sf);

  for (i=0;i<DECK_SIZE;i++) {
    gCard[i].Shuffle[0] = gRecord[i][0];
    gCard[i].Shuffle[1] = gRecord[i][1];
    gCard[i].Shuffle[2] = gRecord[i][2];
    gCard[i].Title[0] = gRecord[i][3];
    gCard[i].Title[1] = gRecord[i][4];
    gCard[i].Rank = gRecord[i][5];
    gCard[i].Suit = gRecord[i][6];
    if (gRecord[i][9] == 'T')
         gCard[i].IsWild = true;
    else gCard[i].IsWild = false;
    if (gRecord[i][7] == ' ') gS[0] = '0'; else gS[0] = gRecord[i][7];
    if (gRecord[i][8] == ' ') gS[1] = '0'; else gS[1] = gRecord[i][8];
    gS[2] = 0x00;
    gCard[i].Value = atoi(gS);
  }
}

/*

This function sorts the specified hand.

*/

void far SortHand(int Who) {
  int i;

  for (i=0;i<DECK_SIZE;i++) {
    sprintf(gRecord[i],"%c",gHand[Who][i].Rank);
    if (gHand[Who][i].Index == EMPTY)
         sprintf(gRecord[i]+1,"999");
    else sprintf(gRecord[i]+1,"%3d",gHand[Who][i].Index);
    if (gHand[Who][i].Selected)
         sprintf(gRecord[i]+4,"T");
    else sprintf(gRecord[i]+4,"F");
    gRecord[i][5] = 0x00;
  }

  qsort((void *)gRecord, DECK_SIZE, sizeof(gRecord[0]), sf);

  for (i=0;i<DECK_SIZE;i++) {
    gHand[Who][i].Rank = gRecord[i][0];
    if (gRecord[i][4] == 'T')
         gHand[Who][i].Selected = true;
    else gHand[Who][i].Selected = false;
    if (gRecord[i][1] == ' ') gS[0] = '0'; else gS[0] = gRecord[i][1];
    if (gRecord[i][2] == ' ') gS[1] = '0'; else gS[1] = gRecord[i][2];
    if (gRecord[i][3] == ' ') gS[2] = '0'; else gS[2] = gRecord[i][3];
    gS[3] = 0x00;
    gHand[Who][i].Index = atoi(gS);
    if (gHand[Who][i].Index == 999) gHand[Who][i].Index = EMPTY;
  }
}

/*

This function starts a new round.

*/

void far StartOver() {
  int i,j,k;

  i=j=k=0;

  // Reset global variables

  NextCardBack();
  gNextCardInStock = DECK_SIZE-1;
  gTopPile = k = EMPTY;
  gEndRound = false;
  gChanged = true;
  gPhase = 0;
// 08Nov2010 Next two lines added
  gpMeldedBefore = false;
  gcMeldedBefore = false;

  // Create Card Deck.

  for (i=0; i<DECK_SIZE-4; i++ ) {
    j = i%13;
    itoa(rand() % RAND_MAX,gCard[i].Shuffle,36);
    gCard[i].Title[0] = gRankString[j];
    gCard[i].Rank = 'a'+(13-j);
    if (j == 0) {
      k++;
      k %= 4;
    }
    gCard[i].Title[1] = gSuitString[k];
    gCard[i].Title[2] = 0x00;
    gCard[i].Suit = gSuitString[k];
    switch (gCard[i].Title[0]) {
    case '3': case '4': case '5': case '6': case '7':
      gCard[i].Value = 5;
      gCard[i].IsWild = false;
      break;
    case '8': case '9': case 'T': case 'J': case 'Q': case 'K':
      gCard[i].Value = 10;
      gCard[i].IsWild = false;
      break;
    case 'A':
      gCard[i].Value = 20;
      gCard[i].IsWild = false;
      break;
    case '2':
      gCard[i].Value = 20;
      gCard[i].IsWild = true;
      break;
    }
  }

  // Add jokers

  for (; i<DECK_SIZE; i++ ) {
    itoa(rand() % RAND_MAX,gCard[i].Shuffle,36);
    gCard[i].Title[0] = 'Z';
    if ((i%2) == 0)
      gCard[i].Title[1] = '1';
    else
      gCard[i].Title[1] = '2';
    gCard[i].Title[2] = 0x00;
    gCard[i].Rank = 'a';
    gCard[i].Suit = '*';
    gCard[i].Value = 50;
    gCard[i].IsWild = true;
  }

  ShuffleDeck();

  // Clear the Table.

  for (i=0;i<NUM_PLAYERS;i++) {
    for (j=0;j<MELD_LOCATIONS;j++) {
      gMeld[i][j].IsBook = false;
      gMeld[i][j].HasWild = false;
      for (k=0;k<MELD_DEPTH;k++) {
        gMeld[i][j].Position[k] = EMPTY;
      }
    }
  }
  for (i=0;i<DECK_SIZE;i++) {
    gStock[i] = i;
    gDiscard[i] = EMPTY;
    gHand[COMPUTER][i].Index = EMPTY;
    gHand[COMPUTER][i].Rank = '~';
    gHand[COMPUTER][i].Selected = false;
    gHand[PLAYER][i].Index = EMPTY;
    gHand[PLAYER][i].Rank = '~';
    gHand[PLAYER][i].Selected = false;
  }

  // Deal

  gpHandCardCount = 0;
  gcHandCardCount = 0;
  for (i=0;i<15;i++) {
    for (j=0;j<NUM_PLAYERS;j++) {
      gHand[j][i].Index = DrawCard(j);
      gHand[j][i].Rank = gCard[gHand[j][i].Index].Rank;
      if (j == PLAYER)   gpHandCardCount++;
      if (j == COMPUTER) gcHandCardCount++;
    }
  }
  SortHand(COMPUTER);
  SortHand(PLAYER);

  // Turn up first upcard from stock

  gTopPile++;
  gDiscard[gTopPile] = gStock[gNextCardInStock];
  gStock[gNextCardInStock] = EMPTY;
  gNextCardInStock--;
}

/*

This function checks for wild or three on discard pile, asks user
for a meld, checks meld, sorts hand, moves all discard pile to hand,
erases discard pile, and forces a "draw card" if illegal meld.

*/

bool far pTake() {
  int i,d;
  char a,b;

  i=d=0;
  a=b=' ';
  if (!(gpMeldedBefore)) return false;
  if (gTopPile == EMPTY) return false;
  b = gCard[gDiscard[gTopPile]].Title[0];

  switch (b) {
  case 'Z':
  case '2':
  case '3':
    return false;
  }
  a = pMeld(true);
  if (a == ' ') return false;
  if (!(pMinLegalMeld(true))) return false;
  if (a == b) {
    for (i=0;i<DECK_SIZE;i++) {
      if (gHand[PLAYER][i].Index == EMPTY) {
        break;
      }
    }
    for (;;) {
      d = gDiscard[gTopPile];
      gDiscard[gTopPile] = EMPTY;
      gTopPile--;
      gHand[PLAYER][i].Index = d;
      gHand[PLAYER][i].Rank = gCard[d].Rank;
      gHand[PLAYER][i].Selected = false;
      gpHandCardCount++;
      if (gTopPile == EMPTY) break;
      i++;
    }
    SortHand(PLAYER);
  }
  else {
    pDraw();
    return true;
  }
  return true;
}

/*

This function tries to take the discard pile using the computer hand.

*/

bool far cTryTakeDiscard() {
  int CardList[20];
  int i, j, k;
  int MeldPit;
  int MeldList[8];
  char NatToMeld = gCard[gDiscard[gTopPile]].Title[0];
  int NatsInHand = 0;
  char RankOfCardInList;
  int Score = gCard[gDiscard[gTopPile]].Value;
  int WildList[12];
  int WldInHand = 0;
  int DeckIndex;

  if (gTopPile == EMPTY) return false;
  switch ( NatToMeld ) {
  case 'Z':
  case '2':
  case '3':
    return false;
  }
  for (i=0; i<DECK_SIZE; i++) {
    DeckIndex = gHand[COMPUTER][i].Index;
    if ( DeckIndex == EMPTY ) return false;
    RankOfCardInList = gCard[DeckIndex].Title[0];
    if ( RankOfCardInList == NatToMeld ) break;
  }
  for (i=0; i<MELD_DEPTH; i++) CardList[i] = EMPTY;
  for (i=0; i<8; i++) MeldList[i] = EMPTY;
  for (i=0; i<12; i++) WildList[i] = EMPTY;
  MeldList[0] = gDiscard[gTopPile];
  MeldPit = cFindMeldPit( NatToMeld );
  for (i=0; i<DECK_SIZE; i++) {
    DeckIndex = gHand[COMPUTER][i].Index;
    if ( DeckIndex == EMPTY ) break;
    RankOfCardInList = gCard[DeckIndex].Title[0];
    switch ( RankOfCardInList ) {
    case 'Z':
    case '2':
      WildList[WldInHand++] = DeckIndex;
    }
    if ( RankOfCardInList == NatToMeld )
      MeldList[++NatsInHand] = DeckIndex;
  }
  if ( gWildInDiscardPile ) {
    if ( MeldPit == EMPTY ) {
      if ( NatsInHand < 2 ) return false;
    }
  }
  else {
    if ( MeldPit == EMPTY ) {
      if ( WldInHand >= 1 ) {
        WldInHand = 1;
        NatsInHand = 1;
      }
      else {
        if ( NatsInHand < 2 )  return false;
        else {
          NatsInHand = 2;
        }
      }
    }
  }
  for (i=0; i<NatsInHand; i++) {
    DeckIndex = MeldList[i+1];
    if ( DeckIndex == EMPTY ) break;
    CardList[i] = DeckIndex;
    Score += gCard[DeckIndex].Value;
  }
  for ( j=0; j<WldInHand; j++ ) {
    DeckIndex = WildList[j];
    if ( DeckIndex == EMPTY ) break;
    CardList[i + j] = DeckIndex;
    Score += gCard[DeckIndex].Value;
  }
  if ( !gcMeldedBefore ) {
    if ( Score >= cMinLegalMeld() ) {
      if (( NatsInHand + WldInHand ) >= 2 )
        gcMeldedBefore = true;
      else return false;
    }
    else return false;
  }
  if ( MeldPit == EMPTY ) {
    switch (NatToMeld) {
    case '3': MeldPit= 0; break;
    case '4': MeldPit= 1; break;
    case '5': MeldPit= 2; break;
    case '6': MeldPit= 3; break;
    case '7': MeldPit= 4; break;
    case '8': MeldPit= 5; break;
    case '9': MeldPit= 6; break;
    case 'T': MeldPit= 7; break;
    case 'J': MeldPit= 8; break;
    case 'Q': MeldPit= 9; break;
    case 'K': MeldPit=10; break;
    case 'A': MeldPit=11; break;
    }
  }
  for (i=0; i<MELD_DEPTH; i++) {
    DeckIndex = gMeld[COMPUTER][MeldPit].Position[i];
    if ( DeckIndex == EMPTY ) break;
  }
  for ( j=0; j<WldInHand; j++ ) {
    DeckIndex = WildList[j];
    if ( DeckIndex == EMPTY ) break;
    gMeld[COMPUTER][MeldPit].Position[i+j] = DeckIndex;
    gMeld[COMPUTER][MeldPit].HasWild = true;
  }
  for ( k=0; k<=NatsInHand; k++ ) {
    DeckIndex = MeldList[k];
    if ( DeckIndex == EMPTY ) break;
    gMeld[COMPUTER][MeldPit].Position[i+j+k] = DeckIndex;
  }
  for (i=0; i<20; i++) {
    if ( CardList[i] == EMPTY ) break;
    for ( j=0; j<DECK_SIZE; j++ ) {
      DeckIndex = gHand[COMPUTER][j].Index;
      if ( DeckIndex == CardList[i] ) break;
    }
    gHand[COMPUTER][j].Index = EMPTY;
    gHand[COMPUTER][j].Rank = '~';
    gHand[COMPUTER][j].Selected = false;
    gcHandCardCount--;
  }
  gDiscard[gTopPile] = EMPTY;
  gTopPile--;
  for (i=0; i<DECK_SIZE; i++) {
    DeckIndex = gHand[COMPUTER][i].Index;
    if ( DeckIndex == EMPTY ) break;
  }
  for ( j=0; j<=DECK_SIZE; j++ ) {
    DeckIndex = gDiscard[j];
    if ( DeckIndex == EMPTY ) break;
    gHand[COMPUTER][i+j].Index = DeckIndex;
    gHand[COMPUTER][i+j].Rank = gCard[DeckIndex].Rank;
    gHand[COMPUTER][i+j].Selected = false;
    gcHandCardCount++;
    gDiscard[j] = EMPTY;
  }
  gTopPile = EMPTY;
  gWildInDiscardPile = false;
  SortHand(COMPUTER);

  return true;
}

/*

This function is used to wait exactly the seconds specified.

*/

void far WaitASec() {
  time_t t, tSave;

  t = time( NULL );
  tSave = t + 1.75;
  while ( tSave > t ) t = time( NULL );
}

/*

This function returns where a card is located in the computer hand.

*/

int far cWhereInHand( int Object ) {
  int i;
  int Result = EMPTY;
  int DeckIndex;

  for (i=0;i<DECK_SIZE;i++) {
    DeckIndex = gHand[COMPUTER][i].Index;
    if (DeckIndex == EMPTY) break;
    if (DeckIndex == Object) {
      Result = i;
      break;
    }
  }

  return Result;
}

/* ***************************************************************** */

/*

This function constructs the time zone, the graphic environment, random
number sequencing, the mouse environment, and the scorepad.

*/

void far ProgramConstructor() {
  int i,j,GraphError;
  int GraphDevice = VGA;
  int GraphMode = VGAHI;

  i=j=GraphError=0;
  putenv("TZ=PST8PDT");
  tzset();

  initgraph( &GraphDevice, &GraphMode, PATH_TO_BGI );
  GraphError = graphresult();
  if( GraphError != grOk ){
    pd2();
    printf("Path to BGI files: \"%s\".\n", PATH_TO_BGI );
    printf("Graphics error in %s:\n", PROGNAME);
    printf("%s\nPress a key to continue...\n",
      grapherrormsg( GraphError ) );
    getch();
    exit( 5 );
  }
  settextstyle(DEFAULT_FONT, HORIZ_DIR, 1);
  gTextHeight = textheight( "H" );
  gTextWidth = textwidth( "M" );

  srand((unsigned) time(NULL));

#ifdef USE_MOUSE
  MouseInit( &gMouseInformation );
  if ( !gMouseInformation.Exist ) {
    ProgramDestructor();
    printf("Error in %s: The mouse does not exist.\n", PROGNAME);
    printf("The mouse is needed for this program.\n");
    printf("Press a key to continue...\n");
    getch();
    exit( 6 );
  }
#endif
  for (i=0;i<MAX_ROUNDS;i++) {
    for (j=0;j<NUM_PLAYERS;j++) {
      gBonusPoints[i][j] = 0;
      gMeldPoints[i][j]  = 0;
      gScore[i][j]       = 0;
    }
  }
  StartOver();
}

/*

This function is the main loop. It refreshes the graphic screen
if changed, processes the end of round and the end of game, reads
the desktop menu from the user, and processes the desktop menu
options.

*/

bool far MainLoop() {
  char Answer[3] = "  ";

  if (gChanged) Refresh();
  gChanged = false;
  if (gEndRound) {
    FigureScore(gRounds-1);
    Gprintf( 0, 1, BLACK, WHITE, " End of Round               ");
    Gprintf( 1, 1, BLACK, WHITE, " Press a key to continue... ");
    gRounds++;
    ShowScore();
    getch();
    if (gEndGame) {
      cleardevice();
      Gprintf( 0, 1, BLACK, WHITE, " End of Game!               ");
      Gprintf( 1, 1, BLACK, WHITE, " Press a key to continue... ");
      ShowScore();
      getch();
      return false;
    }
    StartOver();
    Refresh();
    Gprintf( 1, 1, BLACK, WHITE, " New Round                  ");
  }
  Answer[0] = ReadDesktop();
  switch (Answer[0]) {
  case 0x1B: // Esc
  case 'e': // Exit
    ProgramDestructor();
    exit( 7 );
    break;
  case 'h': // Help
    Answer[1] = ReadMenu(gHelpMenu,HELP_PULLDOWN_COUNT);
    if (Answer[1] == 'a') About();
    gChanged = true;
    break;
  default:
    switch (gPhase) {
    case 0:
      switch (Answer[0]) {
      case 't': // Take
        if (pTake()) gPhase = 1;
        /* Failure to take repeats Phase 0 */
        gChanged = true;
        break;
      case 'd': // Draw
        if (pDraw()) gPhase = 1;
        /* Failure to draw repeats Phase 0 */
        gChanged = true;
        break;
      case 'r': // Restore
        RestoreStateOfComputer();
        break;
      case 's': // Save
        SaveStateOfComputer();
        break;
      }
      break;
    case 1:
      switch (Answer[0]) {
      case 'm': // Meld
        pMeld(false);
        gChanged = true;
        break;
      case 'd': // Discard
        if (pDiscard()) ComputerTurn();
        gChanged = true;
        break;
      }
      break;
    }
  }

  return true;
}

/*

This function closes the graphic environment and clears the text screen.

*/

void far ProgramDestructor() {
  closegraph();
  pd2();
}

/*

This function is the partial destructor that clears the text screen.

*/

void far pd2() {
  textmode( C4350 );
  textcolor( LIGHTGRAY );
  textbackground( BLACK );
  clrscr();
}

/*

This function assists the qsort function call.

*/

int far sf( const void *a, const void *b) {
   return( strcmp((char *)a,(char *)b) );
}

// END OF FILE: GCANASTA.CPP


```

---

### Post by Tony Flury on 2011-07-18
I think the point that nvteighen and other will make is that : 
yes - you have renamed some functions and variables, but you have not actually done anything structural to improve your program.

Even if you don't do anything Object Oriented, then you should at least try and write good procedural code - i.e. each function has clear attributes, clear return values, a well defined behaviour (only defined by the attributes and return values), and no side effects (or minimal side effects). This is called encapsulation.

When you encapsulate your code - as already mentioned - you will be able to track down your problems a lot more easily.

---

### Post by schauerlich on 2011-07-18
I'm inclined to agree with nvteighen. While I understand you're apprehensive to throw away code you've worked hard on, it's simply an unmaintainable mess at this point.

---

### Post by machdohvah on 2011-07-18
> **Tony Flury said:**
> I think the point that nvteighen and other will make is that : 
yes - you have renamed some functions and variables, but you have not actually done anything structural to improve your program.

Even if you don't do anything Object Oriented, then you should at least try and write good procedural code - i.e. each function has clear attributes, clear return values, a well defined behavior (only defined by the attributes and return values), and no side effects (or minimal side effects). This is called encapsulation.

When you encapsulate your code - as already mentioned - you will be able to track down your problems a lot more easily.

I would like to quote from a book as this "encapsulation" concept is new to me. From "Code Complete: A Practical Handbook of Software Construction" by Steve McConnell, published by Microsoft 1993, ISBN: 1-55615-454-4, starting at page 118:

> 
6.2 Information Hiding

If you've been reading the cross-references throughout this book, you've probably noticed about 400 references to information hiding. With that many references, it had better be important.

It is.

The idea of information hiding comes into play at all levels of design, from the use of named constants instead of literals, to routine design, to module and program design. Because the idea is often best applied at the module level, it's discussed at length in this chapter.

Hiding information is one of the few theoretical techniques that has indisputably proven its value in practice (Boehm 1978a). Large programs that use information hiding have been found to be easier to modify -- by a factor of 4 -- than programs that don't (Korson and Vaihnavi 1986). Moreover, information hiding is part of the foundation of both structured design and object-oriented design. In structured design, the notion of black boxes comes from information hiding. In object-oriented design, information hiding gives rise to the notions of encapsulation and abstraction.



I will read further and not bore you with quoting more of it. Fascinating!

---

### Post by nvteighen on 2011-07-18
> **machdohvah said:**
> Please expand on "encaosulation" for this might actually be helpful.


There are different opinions on what constitutes encapsulation, but there are some common ideas shared by everyone. Encapsulation is isolating stuff behind interfaces... in practice, it's synomymous to abstraction. And usually, it's associated to OOP and sometimes, associated to some features of the Java or C++ OOP.

Assume you have the following interface (this could be part of a C header file):
```

/* Assume card, suit, value as C types */

card *new_card(suit card_suit, value card_value);
suit card_get_suit(card *the_card);
value card_get_value(card *the_card);
int is_card_higher(card *card1, card *card2);
int is_card_equal(card *card2, card *card2);
int is_card_lower(card *card1, card *card2);
void destroy_card(card *some_card);

```

Pretty straightforward, isn't it? I bet you can get guess what each function does without further documentation. Do you know how it is implemented? No, new_card returns a pointer... that could hide anything. Do you actually care how it is implemented, as long as each function does what it's intended to? No. You may guess though, that some suit and some value attribute is "inside" the card data type, but you don't know if there's something else. For example, the comparing functions may work by using some internal data that's calculated by new_card and that you don't have any external control for.

1) That's OOP done in C. 2) That's encapsulation: you've created an interface thar controls how you interact with the card data type... or card 'class'. Moreover, you could change the implementation without affecting the interface and therefore, not changing the code that uses this data type! 

But in that snippet there's an issue. I know you know what structs are... and you surely know that you can access any struct's member using the variable.member syntax, because struct's have all their members set to public. In C, one way to force "privacy" is by using a very hackish compiler technique called "Opaque Pointers". In C++, classes allow you to mark different attributes as public, private or protected (forget that last one for now). For *some people* privacy is essential for true encapsulation; for others like myself, it isn't (I consider variable.member to be an interface too).

The best way to learn this is to start programming around data types, like they were "types of objects" (i.e. classes). You create a class, you define ways to interact with that class and you create objects that are of that class... That provides almost instant encapsulation, whether the attributes are public or private. As long as you follow the interface you define, "the contract" (in the wise words of Sussman and Abelson...), you'll be fine...

... of course, you have to learn how to write good interfaces that make your life easier... and that's only achieved by practice. I myself keep creating stupid ones...

---

### Post by machdohvah on 2011-07-18
> **nvteighen said:**
> There are different opinions on what constitutes encapsulation, but there are some common ideas shared by everyone. Encapsulation is isolating stuff behind interfaces... in practice, it's synomymous to abstraction. And usually, it's associated to OOP and sometimes, associated to some features of the Java or C++ OOP.

...

... of course, you have to learn how to write good interfaces that make your life easier... and that's only achieved by practice. I myself keep creating stupid ones...

Excuse me for saying this, but that was very confusing. I am starting over with a test program to attempt to learn this concept, but in so doing, I am getting errors thatI do not understand.

```
Error TEST.CPP...Line 47:
Improper use of typedef 'PixelFile':
Your source file use a typedef symbol where a variable should appear is an expression.
Check for the declaration of the symbel and possible misspellings.
```

and here is my current TEST.CPP with 25 errors with the first error listed above.

```


#define PROGNAME "TEST.CPP" 
#define VERSION "18JUL2011" 
#define AUTHOR "Michael Flower" 
 
/* 
 
This is an attempt to learn how encapsulation and abstraction works. 
 
*/ 
 
#include <conio.h> 
#include <graphics.h> 
#include <stdio.h> 
#include <stdlib.h> 
#include <string.h> 
 
/* *** */ 
 
enum bool {false, true}; 
 
/* *** */ 
 
class GraphicEnv { 
public: 
  int GraphError; 
  int GraphDevice; 
  int GraphMode; 
  GraphicEnv(); 
  ~GraphicEnv(); 
  char *Path; 
}; 
 
class PixelFile { 
public: 
  char *Path; 
  void Show(char *, int, int, bool); 
}; 
 
/* *** */ 
 
void AbEnd(int,char); 
 
/* *** */ 
 
int main() { 
  GraphicEnv(); 
  PixelFile.Show("AS.PXL", 1, 1, false); 
 
  getch(); 
 
  ~GraphicEnv(); 
 
  return 0; 
} 
 
/* *** */ 
 
void AbEnd(int l, char *s) { 
  ~GraphicEnv(); 
  printf(1,1,"%s (version %s, author %s) ",PROGNAME, VERSION, AUTHOR); 
  printf(1,1,"aborted on line %d for this reason:\n\n",l); 
  printf(2,1,"%s\n\n",s); 
  printf(3,1,"Press enter to continue..."); 
  getch(); 
  exit(1); 
} 
 
GraphicEnv::GraphicEnv() { 
  strcpy(Path,"\\TC\\BGI"); 
  GraphDevice = VGA; 
  GraphMode = VGAHI; 
  initgraph( &GraphDevice, &GraphMode, Path ); 
  GraphError = graphresult(); 
  if( GraphError != grOk ){ 
    printf("Path to BGI files missing: \"%s\".\n", Path ); 
    printf("Graphics error in %s:\n", PROGNAME); 
    grapherrormsg( GraphError ) ); 
    printf("%s\nPress a key to continue...\n", 
    getch(); 
    exit( 1 ); 
  } 
  settextstyle(DEFAULT_FONT, HORIZ_DIR, 1); 
} 
 
GraphicEnv::~GraphicEnv() { 
  closegraph(); 
  textmode( C4350 ); 
  textcolor( LIGHTGRAY ); 
  textbackground( BLACK ); 
  clrscr(); 
} 
 
void PixelFile::Show(char *FileName, int Row, int Col, bool Sideways) { 
  int Th = textheight( "H" ); 
  int Tw = textwidth( "M" ); 
  int Xref = Col*Tw; 
  int Yref = Row*Th; 
  int x, y, Color; 
  FILE *InFile; 
  int Width; 
  char s[640]=""; 
 
  strcpy(Path,"\\MYDOCS\\TC\\CARDS\\PXL\\"); 
  x=y=Color=Width=0; 
  sprintf(s,"%s%s",Path,FileName); 
  if ( (InFile = fopen(s, "rb")) == NULL ) { 
    sprintf(s,"File not found: %s%s",Path,FileName); 
    AbEnd(__LINE__,s); 
  } 
  else { 
 
  fgets(s, 640, InFile ); 
  while ( !feof(InFile) ) { 
    Width = strlen(s); 
    for (x=0; x<Width; x++) { 
      Color = EMPTY; 
      switch (s[x]) { 
      case '0': Color =  0; break; 
      case '1': Color =  1; break; 
      case '2': Color =  2; break; 
      case '3': Color =  3; break; 
      case '4': Color =  4; break; 
      case '5': Color =  5; break; 
      case '6': Color =  6; break; 
      case '7': Color =  7; break; 
      case '8': Color =  8; break; 
      case '9': Color =  9; break; 
      case 'A': Color = 10; break; 
      case 'B': Color = 11; break; 
      case 'C': Color = 12; break; 
      case 'D': Color = 13; break; 
      case 'E': Color = 14; break; 
      case 'F': Color = 15; 
      } 
      if (Sideways) { 
        if (Color != EMPTY) putpixel( y+312,278-x, Color ); 
      } 
      else { 
        if (Color != EMPTY) putpixel( x+Xref, y+Yref, Color ); 
      } 
    } 
    y++; 
    fgets(s, 640, InFile ); 
  } 
  fclose( InFile ); 
 
  } 
}


```The thing is that it is NOT misspelled and I am not using typedef anywhere. Help! Maybe this is why I stopped looking into "class". :)

---

### Post by worseisworser on 2011-07-18
```

$ g++ -g -Wall -o machdohvah-test machdohvah-test.cpp 
machdohvah-test.cpp:11:20: fatal error: conio.h: No such file or directory
compilation terminated.

$ 

```

No one can help you, and the reason for this is your real problem.

Your code is non-standard; conio.h is not part of C or C++, and it is neither part of any portable library that I know of today anyway. It doesn't work anywhere except perhaps on the already very small and shrinking island you're holding on to. You're all alone, and you don't know why. ..or do you?

Maybe you could face this new reality, spend some time in this realm. Our realm. Swim _against_ the now tiny dried up stream you've been going down for for the last couple of years alone, then climb on top of the mountain and jump into the much bigger ocean. Yup, roar into the skies, tear your shirt off and dive into the ocean like any free animal would; "I'm not debris".

It is sad to see people struggle for reasons that really don't make sense. Please don't make me sad. I'm angry when I'm sad -- and sometimes things break then. So do the right thing; solve your problem. Deal with reality, and tackle things in the right order -- for it is the only way.


edit:
Also your compiler is probably buggy because it is old and outdated. This happens, and this is again why people stay up to date with regards to software; even (or in particular) compilers.

---

### Post by PaulM1985 on 2011-07-18
I think your first error message is a little bit cryptic.  I think the actual issue is that you are trying to call a non-static function in a static way.

I am not sure how comfortable you are with OO programming....

You probably want to be doing something like:

```

PixelFile pixelFile;    // This creates an object of the PixelFile class called pixelFile.
pixelFile.Show("AS.PXL", 1, 1, false);  // This executes the Show function on your object of the PixelFile class which is called pixelFile. 

```

Here is a link which discusses the difference between a class and an object.  [http://www.felgall.com/obj1.htm](http://www.felgall.com/obj1.htm)  Sorry, if you already know this.

Paul

---

### Post by PaulM1985 on 2011-07-18
Also, a couple of other things:

1.
```

enum bool {false, true}; 

```
Why are you creating a boolean enum?  bool already exists, this isn't needed. 

2.
```

  GraphicEnv(); 
  PixelFile.Show("AS.PXL", 1, 1, false); 
 
  getch(); 
 
  ~GraphicEnv(); 

```

I see what you are trying to do here with GraphicEnv.  You are trying to set something up and have it unset once the program finishes.
If you create an object, using:
GraphicEnv myGraphics;
This will create an object, called myGraphics which will call the constructor for you.  When an object runs out of scope, it will automatically call your destructor, so you don't have to :-)

Paul

---

### Post by unknownPoster on 2011-07-18
> **PaulM1985 said:**
>   When an object runs out of scope, it will automatically call your destructor, so you don't have to :-)



I'm no expert on memory management, but I don't think this is true without a garbage collector which C++ does not have. Java and Python handle it this way, but you should always call the destructor in C++.

---

### Post by PaulM1985 on 2011-07-18
> **unknownPoster said:**
> I'm no expert on memory management, but I don't think this is true without a garbage collector which C++ does not have. Java and Python handle it this way, but you should always call the destructor in C++.

Ok, I was talking in the case of objects that aren't pointers.  Pointers need to be deleted, the GraphicsEnv object wasn't a pointer.

From [http://cplus.about.com/od/learning1/ss/cppobjects_9.htm](http://cplus.about.com/od/learning1/ss/cppobjects_9.htm)

"When an object goes out of scope or more rarely is explicitly destroyed, its destructor is called."

---

### Post by nvteighen on 2011-07-18
> **worseisworser said:**
> ```

$ g++ -g -Wall -o machdohvah-test machdohvah-test.cpp 
machdohvah-test.cpp:11:20: fatal error: conio.h: No such file or directory
compilation terminated.

$ 

```

No one can help you, and the reason for this is your real problem.

Your code is non-standard; conio.h is not part of C or C++, and it is neither part of any portable library that I know of today anyway. It doesn't work anywhere except perhaps on the already very small and shrinking island you're holding on to. You're all alone, and you don't know why. ..or do you?

Maybe you could face this new reality, spend some time in this realm. Our realm. Swim _against_ the now tiny dried up stream you've been going down for for the last couple of years alone, then climb on top of the mountain and jump into the much bigger ocean. Yup, roar into the skies, tear your shirt off and dive into the ocean like any free animal would; "I'm not debris".

It is sad to see people struggle for reasons that really don't make sense. Please don't make me sad. I'm angry when I'm sad -- and sometimes things break then. So do the right thing; solve your problem. Deal with reality, and tackle things in the right order -- for it is the only way.


edit:
Also your compiler is probably buggy because it is old and outdated. This happens, and this is again why people stay up to date with regards to software; even (or in particular) compilers.

Most have already pointed out what I wanted to say about the OP's code. But this post by worseisworser quoted here is the nothing more and nothing less than the truth of this case.

---

### Post by machdohvah on 2011-07-19
> **worseisworser said:**
> ```

$ g++ -g -Wall -o machdohvah-test machdohvah-test.cpp 
machdohvah-test.cpp:11:20: fatal error: conio.h: No such file or directory
compilation terminated.

$ 

```No one can help you, and the reason for this is your real problem.

...

Also your compiler is probably buggy because it is old and outdated. This happens, and this is again why people stay up to date with regards to software; even (or in particular) compilers.

There are two problems with g++ that I have had in the past. One, I am not able to stop the action like a can with getch() supported by conio.h, and I have never been successful in finding a function that allows me to place a pixel color in a window. Without those two things, I am not able to do anything. All of my programs are designed to run in "dosbox", and, yes, it runs just fine. I agree that the "class" portion of my small Borland Turbo C++ compiler that is written for DOS 6.20. I have been programming for more than 35 years and am retired.

Here is one of my recent successes and you all may publish a corrected version in your way without care from me. Consider it my gift.

```


#define PROGNAME "PLAY4CAN" 
#define VERSION "18Jul2011" 
#define AUTHOR "Michael Flower" 
 
/* 
 
18Jul2011 New program canibalized from gcanasta.cpp. This is an attempt to 
create a four-player partnership canasta game with the user playing all four 
sides as the table turns. 
 
*/ 
 
// INCLUDES 
 
#include <conio.h> 
#include <ctype.h> 
#include <graphics.h> 
#include <stdarg.h> 
#include <stdio.h> 
#include <stdlib.h> 
#include <string.h> 
#include <time.h> 
 
// DEFINES 
 
#define CARDS_TO_DEAL 11 
#define DECK_SIZE 108 
#define DESKTOP_BUTTON_COUNT 6 
#define DISCARD_PULLDOWN_COUNT 15 
#define EMPTY -1 
#define GAME_PULLDOWN_COUNT 1 
#define HELP_PULLDOWN_COUNT 1 
#define MAX_ROUNDS 8 
#define MELD_DEPTH 15 
#define MELD_DISPLAY_MARGIN 7 
#define MELD_DISPLAY_WIDTH 5 
#define MELD_LOCATIONS 12 
#define MELD_PULLDOWN_COUNT 15 
#define NATURAL_RANK_PULLDOWN_COUNT 11 
#define NUMBER_CANASTA_OUT 2 
#define NUMBER_CARDS_DRAW 1 
#define STATUS_FOR 14 
#define STATUS_BACK 6 
#define STATUS_LINE 59 
#define STOCK_COLUMN 30 
#define STOCK_ROW 24 
 
#define PATH_TO_BGI "\\TC\\BGI" 
#define PATH_TO_CARDS "\\MYDOCS\\TC\\CARDS\\PXL\\" 
 
// ENUMERATORS 
 
enum {NORTH_P, EAST_P, SOUTH_P, WEST_P, NUM_PLAYERS}; 
enum {NS_SIDE, EW_SIDE, NUM_SIDES}; 
enum bool {false, true}; 
 
// CLASSES 
 
struct cCard { 
  char Shuffle[4], Title[3], Rank, Suit; 
  int Value; 
  bool IsWild; 
}; 
 
cCard far gCard[DECK_SIZE+1]; 
 
struct cHand { 
  char Rank; // for sorting 
  int Index; 
  bool Selected; 
}; 
 
cHand far gHand[NUM_PLAYERS+1][DECK_SIZE+1]; 
 
struct cMeld { 
  bool IsBook; 
  bool HasWild; 
  int Position[MELD_DEPTH+1]; 
}; 
 
cMeld far gMeld[NUM_SIDES+1][MELD_LOCATIONS+1]; 
 
struct cMenu { 
  char letter; 
  char *caption; 
  int row1, col1, row2, col2; 
}; 
 
cMenu far gDesktop[2][DESKTOP_BUTTON_COUNT+1] = { 
  { 
    {'t', " Take ",    0, 0, 0, 5}, 
    {'d', " Draw ",    0, 6, 0,11}, 
    {'s', " Save ",    0,12, 0,17}, 
    {'r', " Restore ", 0,18, 0,26}, 
    {'e', " Exit   ",  0,27, 0,34}, 
    {'h', " Help ",    0,74, 0,79} 
  }, { 
    {'m', " Meld ",    0, 0, 0, 5}, 
    {'d', " Discard ", 0, 6, 0,14}, 
    {'d', "      ",    0,15, 0,20}, 
    {'d', "         ", 0,21, 0,29}, 
    {'e', " Exit   ",  0,30, 0,37}, 
    {'h', " Help ",    0,74, 0,79} 
  } 
}; 
 
cMenu far gDiscardMenu[DISCARD_PULLDOWN_COUNT+1] = { 
  {'3'," 3 Three ", 2, 6, 2,14}, 
  {'4'," 4 Four  ", 3, 6, 3,14}, 
  {'5'," 5 Five  ", 4, 6, 4,14}, 
  {'6'," 6 Six   ", 5, 6, 5,14}, 
  {'7'," 7 Seven ", 6, 6, 6,14}, 
  {'8'," 8 Eight ", 7, 6, 7,14}, 
  {'9'," 9 Nine  ", 8, 6, 8,14}, 
  {'t'," T Ten   ", 9, 6, 9,14}, 
  {'j'," J Jack  ",10, 6,10,14}, 
  {'q'," Q Queen ",11, 6,11,14}, 
  {'k'," K King  ",12, 6,12,14}, 
  {'a'," A Ace   ",13, 6,13,14}, 
  {'2'," 2 Two   ",14, 6,14,14}, 
  {'z'," Z Joker ",15, 6,15,14}, 
  {'x'," X DONE  ",16, 6,16,14} 
}; 
 
cMenu far gHelpMenu[HELP_PULLDOWN_COUNT+1] = { 
  {'a'," About PLAY4CAN ", 2,63, 2,78} 
}; 
 
cMenu far gMeldMenu[MELD_PULLDOWN_COUNT+1] = { 
  {'3'," 3 Three ", 2, 1, 2, 9}, 
  {'4'," 4 Four  ", 3, 1, 3, 9}, 
  {'5'," 5 Five  ", 4, 1, 4, 9}, 
  {'6'," 6 Six   ", 5, 1, 5, 9}, 
  {'7'," 7 Seven ", 6, 1, 6, 9}, 
  {'8'," 8 Eight ", 7, 1, 7, 9}, 
  {'9'," 9 Nine  ", 8, 1, 8, 9}, 
  {'t'," T Ten   ", 9, 1, 9, 9}, 
  {'j'," J Jack  ",10, 1,10, 9}, 
  {'q'," Q Queen ",11, 1,11, 9}, 
  {'k'," K King  ",12, 1,12, 9}, 
  {'a'," A Ace   ",13, 1,13, 9}, 
  {'2'," 2 Two   ",14, 1,14, 9}, 
  {'z'," Z Joker ",15, 1,15, 9}, 
  {'x'," X DONE  ",16, 1,16, 9} 
}; 
 
cMenu far gNatualRankMenu[NATURAL_RANK_PULLDOWN_COUNT+1] = { 
  {'4'," 4 Four  ", 3, 6, 3,14}, 
  {'5'," 5 Five  ", 4, 6, 4,14}, 
  {'6'," 6 Six   ", 5, 6, 5,14}, 
  {'7'," 7 Seven ", 6, 6, 6,14}, 
  {'8'," 8 Eight ", 7, 6, 7,14}, 
  {'9'," 9 Nine  ", 8, 6, 8,14}, 
  {'t'," T Ten   ", 9, 6, 9,14}, 
  {'j'," J Jack  ",10, 6,10,14}, 
  {'q'," Q Queen ",11, 6,11,14}, 
  {'k'," K King  ",12, 6,12,14}, 
  {'a'," A Ace   ",13, 6,13,14} 
}; 
 
// FUNCTION DECLARATIONS 
 
void far mlfAbort(int,char *); 
void far AboutThisProgram(); 
int  far CalcFirstMeld(); 
void far DeselectAllInHand(int); 
bool far Discard(); 
void far DisplayCard(int,int,int,bool); 
int  far DrawCard(int); 
void far FigureScore(int); 
void far GetPixelsFromFile(char *,int,int,bool); 
void far Gprintf(int,int,int,int,char *,...); 
void far HideMenu(cMenu *,int); 
bool far IsRedThree(int,int); 
char far MeldCards(bool); 
bool far MinLegalMeld(bool); 
void far NextCardBack(); 
bool far PlayerDraw(); 
char far ReadDesktop(); 
char far ReadMenu(cMenu *,int); 
void far Refresh(); 
void far RestBehindWin(char *,int,int,int,int); 
void far RestoreState(); 
void far SaveBehindWindow(char *,int,int,int,int); 
void far SaveState(); 
int  far SelectCardInHand(int,char); 
void far ShowMelds(int,int); 
void far ShowMenu(cMenu *,int); 
void far ShowScore(); 
void far ShuffleDeck(); 
void far SortHand(int); 
void far StartOver(); 
bool far TakeDiscardPile(); 
void far WaitASec(); 
 
void far ProgramConstructor(); 
bool far MainLoop(); 
void far ProgramDestructor(); 
void far pd2(); 
 
int far sf(const void *,const void *); 
 
// GLOBAL VARIABLES 
 
int    gActSide; 
int    gActPlayer; 
bool   gChanged = true; 
int    gDealer = WEST_P; 
bool   gEndGame = false; 
bool   gEndRound = false; 
int    gLastCB = 0; 
int    gNextCardInStock = EMPTY; 
int    gPhase = 0; 
int    gRounds = 1; 
int    gTextHeight; 
int    gTextWidth; 
int    gTopPile; 
 
// ARRAYS 
 
int    gHandCardCount[NUM_PLAYERS]; 
int    gCanastaCount[NUM_SIDES]; 
int    gBonusPoints[MAX_ROUNDS+1][NUM_SIDES+1]; 
int    gDiscard[DECK_SIZE+1]; 
bool   gMeldedBefore[NUM_SIDES] = {false,false}; 
int    gMeldPoints[MAX_ROUNDS+1][NUM_SIDES+1]; 
int    gScore[MAX_ROUNDS+1][NUM_SIDES+1]; 
int    gStock[DECK_SIZE+1]; 
 
// STRINGS 
 
char * gCardBackFileName = "FILENAME.EXT"; 
char * gRankString = "3456789TJQKA2Z"; 
char * gSuitString = "HDSC"; 
char   gS[80] = ""; 
char   gRecord[DECK_SIZE][80]; 
 
// PROGRAM ENTRY POINT 
 
void main() { 
  ProgramConstructor(); 
  while (MainLoop()); 
  ProgramDestructor(); 
} 
 
// FUNCTIONS 
 
void far mlfAbort(int l, char *s) { 
  cleardevice(); 
  Gprintf(1,1,YELLOW,BLACK,"%s aborted on line %d for this reason:", 
    PROGNAME,l); 
  Gprintf(2,1,YELLOW,BLACK,"%s",s); 
  Gprintf(3,1,YELLOW,BLACK,"Press a key to continue..."); 
  getch(); 
  ProgramDestructor(); 
} 
 
void far AboutThisProgram() { 
  int i=0; 
 
  SaveBehindWindow("ABTSAVE.DTA",25,26,38,54); 
  Gprintf(25,26, BLACK, WHITE, "ÚÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄ¿"); 
  Gprintf(26,26, BLACK, WHITE, "³ %s                 ³%c",PROGNAME, 
    0xB2); 
  Gprintf(27,26, BLACK, WHITE, "³ %s                ³%c", VERSION, 
    0xB2); 
  Gprintf(28,26, BLACK, WHITE, "ÃÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄŽ%c",0xB2); 
  Gprintf(29,26, BLACK, WHITE, "³ This program was written ³%c",0xB2); 
  Gprintf(30,26, BLACK, WHITE, "³ by %s        ³%c",AUTHOR,0xB2); 
  Gprintf(31,26, BLACK, WHITE, "³ and is intended as a     ³%c",0xB2); 
  Gprintf(32,26, BLACK, WHITE, "³ demonstraion only and is ³%c",0xB2); 
  Gprintf(33,26, BLACK, WHITE, "³ not for sale or lease to ³%c",0xB2); 
  Gprintf(34,26, BLACK, WHITE, "³ anyone.                  ³%c",0xB2); 
  Gprintf(35,26, BLACK, WHITE, "ÃÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄŽ%c",0xB2); 
  Gprintf(36,26, BLACK, WHITE, "³ For the rules, see Hoyle ³%c",0xB2); 
  Gprintf(37,26, BLACK, WHITE, "ÀÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÙ%c",0xB2); 
  for (i=27;i<=54;i++) { 
    Gprintf(38, i, BLACK, WHITE, "%c",0xB2); 
  } 
  ReadDesktop(); 
  RestBehindWin("ABTSAVE.DTA",25,26,38,54); 
} 
 
int far CalcFirstMeld() { 
  int Result = 0; 
 
  if (gRounds <= 1) Result = 50; 
  else { 
    if (gScore[gRounds-2][gActSide] >= 3000) Result = 120; 
    else { 
      if (gScore[gRounds-2][gActSide] >= 1500) Result = 90; 
      else { 
        if (gScore[gRounds-2][gActSide] >= 0) Result = 50; 
        else Result = 15; 
      } 
    } 
  } 
 
  return Result; 
} 
 
void far DeselectAllInHand(int Who) { 
  int i=0; 
 
  for (;i<DECK_SIZE;i++) 
    gHand[Who][i].Selected = false; 
} 
 
bool far Discard() { 
  char a = ' '; 
  int c, h; 
 
  c=h=0; 
  if (!(MinLegalMeld(false))) return false; 
  if ( gHandCardCount[gActPlayer] == 1) 
    if ( gCanastaCount[gActSide] < NUMBER_CANASTA_OUT ) return false; 
 
  for (;;) { 
    a = ReadMenu(gDiscardMenu,DISCARD_PULLDOWN_COUNT); 
    if (a == 0x0D) return false; 
    a = toupper(a); 
    if (a == 'X') return false; 
    c = SelectCardInHand(gActPlayer,a); 
    if (c != EMPTY) break; 
  } 
  h = gHand[gActPlayer][c].Index; 
  gHand[gActPlayer][c].Index = EMPTY; 
  gHand[gActPlayer][c].Rank = '~'; 
  gHand[gActPlayer][c].Selected = false; 
  gHandCardCount[gActPlayer]--; 
  gTopPile++; 
  gDiscard[gTopPile] = h; 
  SortHand(gActPlayer); 
  if (gHandCardCount[gActPlayer] <= 0) gEndRound = true; 
 
  return true; 
} 
 
void far DisplayCard( int Card, int Row, int Col, bool Sideways ) { 
  sprintf( gS, "%s.PXL", gCard[Card].Title ); 
  GetPixelsFromFile( gS, Row, Col, Sideways ); 
} 
 
int far DrawCard(int Who) { 
  int Result; 
  bool Continuing = true; 
 
  Result=0; 
  while (Continuing) { 
    if (gNextCardInStock == EMPTY) return EMPTY; 
    Continuing = false; 
    Result = gStock[gNextCardInStock]; 
    gStock[gNextCardInStock] = EMPTY; 
    gNextCardInStock--; 
    if (IsRedThree(Who, Result)) Continuing = true; 
  } 
  return Result; 
} 
 
void far FigureScore(int r) { 
  int c,i,j,k; 
 
  c=i=j=k=0; 
  for (i=0;i<NUM_SIDES;i++) { 
    gBonusPoints[r][i] = 0; 
    for (j=1;j<MELD_LOCATIONS;j++) { 
      if (gMeld[i][j].IsBook) { 
        if(gMeld[i][j].HasWild) 
             gBonusPoints[r][i] += 300; // black canasta 
        else gBonusPoints[r][i] += 500; // red canasta 
      } 
    } 
 
    for (j=0,k=0;j<MELD_DEPTH;j++) { // count red threes 
      c = gMeld[i][0].Position[j]; 
      if (c == EMPTY) { 
        break; 
      } 
      if ((gCard[c].Title[1] == 'H') || 
          (gCard[c].Title[1] == 'D')) { 
        k++; 
      } 
    } 
    gBonusPoints[r][i] += (k*100); // red three award 
 
    gMeldPoints[r][i] = 0; // figure meld points 
    for (j=0;j<MELD_LOCATIONS;j++) { 
      for (k=0;k<MELD_DEPTH;k++) { 
        c = gMeld[i][j].Position[k]; 
        if (c == EMPTY) { 
          break; 
        } 
        gMeldPoints[r][i] += gCard[c].Value; 
      } 
    } 
 
    for (j=0;j<DECK_SIZE;j++) { // deduct for cards in hand 
      c = gHand[i][j].Index; 
      if (c == EMPTY) { 
        if (j==0) { // award 100 for going out 
          gBonusPoints[r][i] += 100; 
        } 
        break; 
      } 
      else { 
        gMeldPoints[r][i] -= gCard[c].Value; 
      } 
    } 
 
    gScore[r][i] = gBonusPoints[r][i] + gMeldPoints[r][i]; 
    if (r > 0) gScore[r][i] += gScore[r-1][i]; 
  } 
  if (gScore[r][NS_SIDE] >= 5000) gEndGame = true; 
  if (gScore[r][EW_SIDE] >= 5000) gEndGame = true; 
  if (r >= MAX_ROUNDS-1)           gEndGame = true; 
} 
 
void far GetPixelsFromFile(char *FileName, int Row, int Col, bool Sideways) { 
  int Xref = Col*gTextWidth; 
  int Yref = Row*gTextHeight; 
  int x, y, Color; 
  FILE *InFile; 
  int Width; 
  char s[640]=""; 
 
  x=y=Color=Width=0; 
  sprintf(s,"%s%s",PATH_TO_CARDS,FileName); 
  if ( (InFile = fopen(s, "rb")) == NULL ) { 
    sprintf(s,"File not found: %s%s",PATH_TO_CARDS,FileName); 
    mlfAbort(__LINE__,s); 
    exit( 1 ); 
  } 
  else { 
 
  fgets(s, 640, InFile ); 
  while ( !feof(InFile) ) { 
    Width = strlen(s); 
    for (x=0; x<Width; x++) { 
      Color = EMPTY; 
      switch (s[x]) { 
      case '0': Color =  0; break; 
      case '1': Color =  1; break; 
      case '2': Color =  2; break; 
      case '3': Color =  3; break; 
      case '4': Color =  4; break; 
      case '5': Color =  5; break; 
      case '6': Color =  6; break; 
      case '7': Color =  7; break; 
      case '8': Color =  8; break; 
      case '9': Color =  9; break; 
      case 'A': Color = 10; break; 
      case 'B': Color = 11; break; 
      case 'C': Color = 12; break; 
      case 'D': Color = 13; break; 
      case 'E': Color = 14; break; 
      case 'F': Color = 15; 
      } 
      if (Sideways) { 
        if (Color != EMPTY) putpixel( y+Xref, Yref+86-x, Color ); 
      } 
      else { 
        if (Color != EMPTY) putpixel( x+Xref, y+Yref, Color ); 
      } 
    } 
    y++; 
    fgets(s, 640, InFile ); 
  } 
  fclose( InFile ); 
 
  } 
} 
 
void far Gprintf( int Row, int Col, int ForColor, int BackColor, 
    char *FormatString, ... ) { 
  va_list ArgPtr; 
  int i=0; 
 
  va_start( ArgPtr, FormatString ); 
  vsprintf( gS, FormatString, ArgPtr ); 
  char BackStr[2] = {0xDB,0x00}; 
  setcolor( BackColor ); 
  for (; i<strlen( gS ); i++) 
    outtextxy( (Col+i) * gTextHeight, Row * gTextWidth, BackStr ); 
  setcolor( ForColor ); 
  outtextxy( Col * gTextHeight, Row * gTextWidth, gS ); 
  va_end( ArgPtr ); 
} 
 
void far HideMenu(cMenu *PullDown, int Entries) { 
  int MenuWidth = strlen(PullDown[0].caption); 
  int Top       = PullDown[0].row1-1; 
  int Left      = PullDown[0].col1-1; 
  int Bottom    = PullDown[Entries-1].row1+1; 
  int Right     = PullDown[Entries-1].col1+MenuWidth; 
 
  RestBehindWin("MENUBACK.DTA", Top, Left, Bottom+1, Right+1); 
} 
 
bool far IsRedThree(int Who, int n) { 
  int d, WhichMeld = Who % 2; 
  bool Result = false; 
 
  if (gCard[n].Title[0] == '3') { 
    switch(gCard[n].Suit) { 
    case 'H': case 'D': // Red three 
      for (d=0;d<MELD_DEPTH;d++) { 
        if (gMeld[WhichMeld][0].Position[d] == EMPTY) { 
          gMeld[WhichMeld][0].Position[d] = n; 
          break; 
        } 
      } 
      Result = true; 
      break; 
    } 
  } 
  return Result; 
} 
 
char far MeldCards(bool ForTake) { 
  int b,c,i,j,n,p,q,r,t,w; 
  int Queue[MELD_DEPTH]; 
  char a,RankOfQueue; 
 
  b=c=n=p=q=r=t=w=0; 
  a=RankOfQueue=' '; 
  for (;q<MELD_DEPTH;q++) Queue[q] = EMPTY; 
  if (ForTake) n=1; 
  for (q=0;q<MELD_DEPTH;q++) { 
    a = ReadMenu(gMeldMenu,MELD_PULLDOWN_COUNT); 
    if (a == 0x0D) break; 
    if (a == 'x') break; 
    a = toupper(a); 
    b = SelectCardInHand(gActPlayer,a); 
    if (b == EMPTY) q--; 
    else { 
      for (i=1;i<=5;i++) { 
        for (j=(22*(i-1));j<(22*i);j++) { 
          if (j>=DECK_SIZE) break; 
          if (gHand[gActPlayer][j].Index != EMPTY) { 
            if (gHand[gActPlayer][j].Selected) { 
              Gprintf( STATUS_LINE-(6-i), (((22*i)-j-1)*3)+15, YELLOW, BLACK, "%c",0xFE); 
            } 
          } 
        } 
      } 
      c = gHand[gActPlayer][b].Index; 
      Queue[q] = c; 
      if (gCard[c].IsWild) { 
        w++; 
      } 
      else { 
        n++; 
        if (RankOfQueue == ' ') RankOfQueue = a; 
        else { 
          if (RankOfQueue != a) { 
            DeselectAllInHand(gActPlayer); 
            return ' '; 
          } 
        } 
      } 
    } 
  } 
  if (RankOfQueue == ' ') { 
    if (ForTake) return ' '; 
    cleardevice(); 
    Gprintf(1,1,YELLOW,BLACK, "On which rank do you want those wilds to be placed?"); 
    a = ReadMenu(gNatualRankMenu,NATURAL_RANK_PULLDOWN_COUNT); 
    RankOfQueue = toupper(a); 
  } 
  switch (RankOfQueue) { 
  case '3': r= 0; break; 
  case '4': r= 1; break; 
  case '5': r= 2; break; 
  case '6': r= 3; break; 
  case '7': r= 4; break; 
  case '8': r= 5; break; 
  case '9': r= 6; break; 
  case 'T': r= 7; break; 
  case 'J': r= 8; break; 
  case 'Q': r= 9; break; 
  case 'K': r=10; break; 
  case 'A': r=11; break; 
  default: 
    DeselectAllInHand(gActPlayer); 
    return ' '; 
  } 
  for(t=0;t<MELD_DEPTH;t++) { 
    p = gMeld[gActSide][r].Position[t]; 
    if (p == EMPTY) break; 
    if (gCard[p].IsWild) 
         w++; 
    else n++; 
  } 
  if ((n+w)<3) { 
    DeselectAllInHand(gActPlayer); 
    return ' '; 
  } 
  else { 
    if (n<w) { 
      DeselectAllInHand(gActPlayer); 
      return ' '; 
    } 
    else { 
      if (ForTake) { 
        gMeld[gActSide][r].Position[t] = gDiscard[gTopPile]; 
        gDiscard[gTopPile] = EMPTY; 
        gTopPile--; t++; 
      } 
      for (q=0;q<MELD_DEPTH;q++,t++) { 
        if (Queue[q] == EMPTY) break; 
        gMeld[gActSide][r].Position[t] = Queue[q]; 
        for (b=0;b<DECK_SIZE;b++) { 
          if (gHand[gActPlayer][b].Index == Queue[q]) break; 
        } 
        gHand[gActPlayer][b].Index = EMPTY; 
        gHand[gActPlayer][b].Rank = '~'; 
        gHand[gActPlayer][b].Selected = false; 
        gHandCardCount[gActPlayer]--; 
      } 
      gMeldedBefore[gActSide] = true; 
      SortHand(gActPlayer); 
    } 
  } 
  DeselectAllInHand(gActPlayer); 
 
  return RankOfQueue; 
} 
 
bool far MinLegalMeld(bool ForTake) { 
  int l,d,c,CurrMeld,MinMeld; 
 
  l=d=c=CurrMeld=MinMeld=0; 
  MinMeld = CalcFirstMeld(); 
  for (l=1;l<MELD_LOCATIONS;l++) { 
    for (d=0;d<=MELD_DEPTH;d++) { 
      c = gMeld[gActSide][l].Position[d]; 
      if (c == EMPTY) break; 
      CurrMeld += gCard[c].Value; 
    } 
  } 
  if ((CurrMeld > 0 ) && (CurrMeld < MinMeld)) { 
    if (ForTake) return false; 
    cleardevice(); 
    Gprintf(1,1,YELLOW,BLACK, 
      "All melds are being return to your hand."); 
    Gprintf(2,1,YELLOW,BLACK,"Press a key to continue."); 
    getch(); 
    gMeldedBefore[gActSide] = false; 
    for (c=0;c<DECK_SIZE;c++) { 
      if (gHand[gActPlayer][c].Index == EMPTY) break; 
    } 
    for (l=1;l<MELD_LOCATIONS;l++) { 
      gMeld[gActSide][l].IsBook = false; 
      gMeld[gActSide][l].HasWild = false; 
      for (d=0;d<=MELD_DEPTH;d++) { 
        if (gMeld[gActSide][l].Position[d] == EMPTY) break; 
        gHand[gActPlayer][c].Index = gMeld[gActSide][l].Position[d]; 
        gHand[gActPlayer][c].Rank = gCard[gHand[gActPlayer][c].Index].Rank; 
        gMeld[gActSide][l].Position[d] = EMPTY; 
        gHandCardCount[gActPlayer]++; 
        c++; 
      } 
    } 
    SortHand(gActPlayer); 
    return false; 
  } 
  return true; 
} 
 
void far NextCardBack() { 
  int a = gLastCB; 
 
  while (a == gLastCB) a = rand() % 32; 
  gLastCB = a; 
  switch (a) { 
  case  0: strcpy(gCardBackFileName, "CB0.PXL");   break; 
  case  1: strcpy(gCardBackFileName, "CB1.PXL");   break; 
  case  2: strcpy(gCardBackFileName, "CB2.PXL");   break; 
  case  3: strcpy(gCardBackFileName, "CB3.PXL");   break; 
  case  4: strcpy(gCardBackFileName, "CB4.PXL");   break; 
  case  5: strcpy(gCardBackFileName, "CB5.PXL");   break; 
  case  6: strcpy(gCardBackFileName, "CB6.PXL");   break; 
  case  7: strcpy(gCardBackFileName, "CB7.PXL");   break; 
  case  8: strcpy(gCardBackFileName, "CB8.PXL");   break; 
  case  9: strcpy(gCardBackFileName, "CB9.PXL");   break; 
  case 10: strcpy(gCardBackFileName, "CBA.PXL");   break; 
  case 11: strcpy(gCardBackFileName, "CBB.PXL");   break; 
  case 12: strcpy(gCardBackFileName, "CBC.PXL");   break; 
  case 13: strcpy(gCardBackFileName, "CBD.PXL");   break; 
  case 14: strcpy(gCardBackFileName, "CBE.PXL");   break; 
  case 15: strcpy(gCardBackFileName, "CBF.PXL");   break; 
  case 16: strcpy(gCardBackFileName, "BYC_0.PXL"); break; 
  case 17: strcpy(gCardBackFileName, "BYC_1.PXL"); break; 
  case 18: strcpy(gCardBackFileName, "BYC_2.PXL"); break; 
  case 19: strcpy(gCardBackFileName, "BYC_3.PXL"); break; 
  case 20: strcpy(gCardBackFileName, "BYC_4.PXL"); break; 
  case 21: strcpy(gCardBackFileName, "BYC_5.PXL"); break; 
  case 22: strcpy(gCardBackFileName, "BYC_6.PXL"); break; 
  case 23: strcpy(gCardBackFileName, "BYC_7.PXL"); break; 
  case 24: strcpy(gCardBackFileName, "BYC_8.PXL"); break; 
  case 25: strcpy(gCardBackFileName, "BYC_9.PXL"); break; 
  case 26: strcpy(gCardBackFileName, "BYC_A.PXL"); break; 
  case 27: strcpy(gCardBackFileName, "BYC_B.PXL"); break; 
  case 28: strcpy(gCardBackFileName, "BYC_C.PXL"); break; 
  case 29: strcpy(gCardBackFileName, "BYC_D.PXL"); break; 
  case 30: strcpy(gCardBackFileName, "BYC_E.PXL"); break; 
  case 31: strcpy(gCardBackFileName, "BYC_F.PXL"); break; 
  } 
} 
 
bool far PlayerDraw() { 
  int c=0, i; 
 
  for (i=0;i<NUMBER_CARDS_DRAW;i++) { 
    c = DrawCard(gActPlayer); 
    if (c == EMPTY) return false; 
    gHand[gActPlayer][DECK_SIZE-(1+i)].Index = c; 
    gHand[gActPlayer][DECK_SIZE-(1+i)].Rank = gCard[c].Rank; 
    gHandCardCount[gActPlayer]++; 
    DisplayCard(c,STOCK_ROW,STOCK_COLUMN-4+(2*i),false); 
  } 
 
  SortHand(gActPlayer); 
  WaitASec(); 
 
  return true; 
} 
 
char far ReadDesktop() { 
  char KeyStroke[3] = ""; 
  bool Continuing=true; 
 
  while ( Continuing ) { 
    KeyStroke[0] = KeyStroke[1] = KeyStroke[2] = 0x00; 
    if ( kbhit() ) { 
      KeyStroke[0] = getch(); 
      if ( KeyStroke[0] == 0x00 ) { 
        KeyStroke[1] = getch(); 
        switch (KeyStroke[1]) { 
        case 34: KeyStroke[0] = 'x'; break; 
        case 24: KeyStroke[0] = 'y'; break; 
        case 35: KeyStroke[0] = 'z'; 
        } 
      } 
      Continuing = false; 
    } 
  } 
  if ( KeyStroke[0] ) { 
    if ((KeyStroke[0] >= 'A') && (KeyStroke[0] <= 'Z')) { 
      // lowercase 
      KeyStroke[0] += ' '; 
    } 
  } 
 
  return KeyStroke[0]; 
} 
 
char far ReadMenu(cMenu *PullDown, int Entries) { 
  char KeyStroke[3]; 
  bool Continuing=true; 
 
  ShowMenu(PullDown,Entries); 
  while ( Continuing ) { 
    KeyStroke[0] = KeyStroke[1] = KeyStroke[2] = NULL; 
    if ( kbhit() ) { 
      KeyStroke[0] = getch(); 
      if ( KeyStroke[0] == NULL ) KeyStroke[1] = getch(); 
      Continuing = false; 
    } 
  } 
  if ( KeyStroke[0] ) { 
    if ((KeyStroke[0] >= 'A') && (KeyStroke[0] <= 'Z')) { 
      // lowercase 
      KeyStroke[0] += ' '; 
    } 
  } 
  HideMenu(PullDown,Entries); 
 
  return KeyStroke[0]; 
} 
 
void far Refresh() { 
  int i,j,k,a,n; 
  int HandL, HandT, HandR, SideOp; 
 
  i=j=k=a=n=0; 
  cleardevice(); 
 
/* 
 
  Special case: Search for red threes in all four hands to correct for 
  taking pile with a red three at bottom from begining of round. 
 
*/ 
  for (k=0;k<NUM_PLAYERS;k++) { 
    for (i=DECK_SIZE-1;i>=0;i--) { 
      n = gHand[k][i].Index; 
      if (n != EMPTY) { 
        if (IsRedThree(k,n)) { 
          gHand[k][i].Index = EMPTY; 
          gHand[k][i].Rank = '~'; 
          gHand[k][i].Selected = false; 
          SortHand(k); 
        } 
      } 
    } 
  } 
 
/* 
 
  3 Inactive Hands -- only the bottom row card backs in two rows 
  for 108 cards 
 
*/ 
 
  switch (gActPlayer) { 
  case NORTH_P: 
    HandL = EAST_P; 
    HandT = SOUTH_P; 
    HandR = WEST_P; 
    SideOp = EW_SIDE; 
    break; 
  case EAST_P: 
    HandL = SOUTH_P; 
    HandT = WEST_P; 
    HandR = NORTH_P; 
    SideOp = NS_SIDE; 
    break; 
  case SOUTH_P: 
    HandL = WEST_P; 
    HandT = NORTH_P; 
    HandR = EAST_P; 
    SideOp = EW_SIDE; 
    break; 
  case WEST_P: 
    HandL = NORTH_P; 
    HandT = EAST_P; 
    HandR = SOUTH_P; 
    SideOp = NS_SIDE; 
    break; 
  } 
 
// Left 
  gHandCardCount[HandL] = 0; 
  // 2nd row 
  for (i=DECK_SIZE-1;i>=54;i--) { 
    n = gHand[HandL][i].Index; 
    if (n != EMPTY) { 
      gHandCardCount[HandL]++; 
      GetPixelsFromFile( gCardBackFileName, (107-i)-6, -10, true ); 
    } 
  } 
// 1st row 
  for (i=53;i>=0;i--) { 
    if (gHand[HandL][i].Index != EMPTY) { 
      gHandCardCount[HandL]++; 
      GetPixelsFromFile( gCardBackFileName, (53-i)-6, -8, true ); 
    } 
  } 
 
// Top 
  gHandCardCount[HandT] = 0; 
  for (i=DECK_SIZE-1;i>=54;i--) { 
    n = gHand[HandT][i].Index; 
    if (n != EMPTY) { 
      gHandCardCount[HandT]++; 
      GetPixelsFromFile( gCardBackFileName, -7, (107-i)+18, false ); 
    } 
  } 
  for (i=53;i>=0;i--) { 
    if (gHand[HandT][i].Index != EMPTY) { 
      gHandCardCount[HandT]++; 
      GetPixelsFromFile( gCardBackFileName, -9, (53-i)+18, false ); 
    } 
  } 
 
// Right 
  gHandCardCount[HandR] = 0; 
  for (i=DECK_SIZE-1;i>=54;i--) { 
    n = gHand[HandR][i].Index; 
    if (n != EMPTY) { 
      gHandCardCount[HandR]++; 
      GetPixelsFromFile( gCardBackFileName, (107-i)-6, 78, true ); 
    } 
  } 
  for (i=53;i>=0;i--) { 
    if (gHand[HandR][i].Index != EMPTY) { 
      gHandCardCount[HandR]++; 
      GetPixelsFromFile( gCardBackFileName, (53-i)-6, 76, true ); 
    } 
  } 
 
  // Inactive Melds -- all threes as Meld0 
 
  ShowMelds(SideOp,5); 
 
  // Score Pad -- showing written bonus and melds 
 
  ShowScore(); 
 
  // Stock -- with number of cards left 
 
  Gprintf(STOCK_ROW-1,STOCK_COLUMN+3,YELLOW,BLACK,"%3d", 
    gNextCardInStock+1); 
  if (gNextCardInStock >= 0) { 
    GetPixelsFromFile( "DECKSIDE.PXL",    STOCK_ROW, STOCK_COLUMN-1, 
      false ); 
    GetPixelsFromFile( gCardBackFileName, STOCK_ROW, STOCK_COLUMN, 
      false ); 
  } 
 
  // Discard Pile -- with wilds and red threes sideways 
 
  if (gTopPile <= EMPTY) gTopPile = EMPTY; // bug fix 
  for (i=0;i<DECK_SIZE;i++) { 
    a = gDiscard[i]; 
    if (a == EMPTY) break; 
    else { 
      if (gCard[a].IsWild) { 
        DisplayCard(a,STOCK_ROW,STOCK_COLUMN+9,true); 
      } 
      else { 
        if ((gCard[a].Title[0] == '3') && 
           ((gCard[a].Title[1] == 'H') || 
            (gCard[a].Title[1] == 'D'))) { 
          DisplayCard(a,STOCK_ROW,STOCK_COLUMN+9,true); 
        } 
        else DisplayCard(a,STOCK_ROW,STOCK_COLUMN+9,false); 
      } 
    } 
  } 
  Gprintf(STOCK_ROW-1,STOCK_COLUMN+10,YELLOW,BLACK,"%3d",gTopPile+1); 
 
  // Player Melds -- all threes as Meld0 
 
  ShowMelds(gActSide,37); 
 
  /* 
 
  Active Hand -- five rows for 108 cards, last row is hardly ever 
  used. The cards have a small designation in the upper right corner. 
 
  */ 
 
  gHandCardCount[gActPlayer] = 0; 
  for (i=1;i<=5;i++) { 
    for (j=(22*(i-1));j<(22*i);j++) { 
      if (j>=DECK_SIZE) break; 
      if (gHand[gActPlayer][j].Index != EMPTY) { 
        gHandCardCount[gActPlayer]++; 
        DisplayCard(gHand[gActPlayer][j].Index, STATUS_LINE-(6-i), 
          (((22*i)-j-1)*3)+7, false); 
      } 
    } 
  } 
 
  // Status Line -- showing all currents 
 
  Gprintf(STATUS_LINE, 0,STATUS_FOR,STATUS_BACK, "%80.80s"," " ); 
  if (gMeldedBefore[gActSide]) { 
    Gprintf(STATUS_LINE, 0,STATUS_FOR,STATUS_BACK, 
      " Round %d |", gRounds ); 
  } else { 
    Gprintf(STATUS_LINE, 0,STATUS_FOR,STATUS_BACK, 
      " Round %d | first meld = %d |", gRounds, (CalcFirstMeld()) ); 
  } 
  switch (gActPlayer) { 
  case NORTH_P: 
    GetPixelsFromFile("EASTWORD.PXL", STOCK_ROW, 1, true); 
    GetPixelsFromFile("SOUTHWRD.PXL", 1, 35, false); 
    GetPixelsFromFile("WESTWORD.PXL", STOCK_ROW, 78, true); 
    GetPixelsFromFile("NORTHWRD.PXL", STATUS_LINE-1, 35, false); 
    break; 
  case EAST_P: 
    GetPixelsFromFile("SOUTHWRD.PXL", STOCK_ROW, 1, true); 
    GetPixelsFromFile("WESTWORD.PXL", 1, 35, false); 
    GetPixelsFromFile("NORTHWRD.PXL", STOCK_ROW, 78, true); 
    GetPixelsFromFile("EASTWORD.PXL", STATUS_LINE-1, 35, false); 
    break; 
  case SOUTH_P: 
    GetPixelsFromFile("WESTWORD.PXL", STOCK_ROW, 1, true); 
    GetPixelsFromFile("NORTHWRD.PXL", 1, 35, false); 
    GetPixelsFromFile("EASTWORD.PXL", STOCK_ROW, 78, true); 
    GetPixelsFromFile("SOUTHWRD.PXL", STATUS_LINE-1, 35, false); 
    break; 
  case WEST_P: 
    GetPixelsFromFile("NORTHWRD.PXL", STOCK_ROW, 1, true); 
    GetPixelsFromFile("EASTWORD.PXL", 1, 35, false); 
    GetPixelsFromFile("SOUTHWRD.PXL", STOCK_ROW, 78, true); 
    GetPixelsFromFile("WESTWORD.PXL", STATUS_LINE-1, 35, false); 
    break; 
  } 
  Gprintf(STATUS_LINE,50,STATUS_FOR,STATUS_BACK, "%s (%s)", PROGNAME, VERSION ); 
 
  // Desktop Menu Bar 
 
  Gprintf( 0, 0, BLACK, WHITE, "%80.80s"," " ); 
  for (i=0;i<DESKTOP_BUTTON_COUNT;i++) { 
    Gprintf(gDesktop[gPhase][i].row1,gDesktop[gPhase][i].col1,BLACK, 
      WHITE, "%s", gDesktop[gPhase][i].caption ); 
    Gprintf(gDesktop[gPhase][i].row1,gDesktop[gPhase][i].col1+1,RED, 
      WHITE, "%c", gDesktop[gPhase][i].caption[1] ); 
  } 
 
  // Check if Player or Computer is out, or if the Stock is empty. 
 
  if (gHandCardCount[NORTH_P] <= 0) gEndRound = true; 
  if (gHandCardCount[EAST_P]  <= 0) gEndRound = true; 
  if (gHandCardCount[SOUTH_P] <= 0) gEndRound = true; 
  if (gHandCardCount[WEST_P]  <= 0) gEndRound = true; 
  if (gNextCardInStock == EMPTY)    gEndRound = true; 
} 
 
void far RestBehindWin(char *FileName, int Top, int Left, 
       int Bottom, int Right) { 
  int i, j; 
  int PixelTop    = Top*gTextHeight; 
  int PixelLeft   = Left*gTextWidth; 
  int PixelBottom = ((Bottom+1)*gTextHeight)-1; 
  int PixelRight  = ((Right+1)*gTextWidth)-1; 
  FILE *InFile; 
  char InChar = ' '; 
 
  i=j=0; 
  if ( (InFile = fopen(FileName, "rb")) == NULL ) { 
    ProgramDestructor(); 
    printf("Error in %s: Cannot open %s file.\n", PROGNAME, FileName); 
    exit( 2 ); 
  } 
 
  for (i=PixelTop;i<=PixelBottom;i++) { 
    for (j=PixelLeft;j<=PixelRight;j++) { 
      InChar = fgetc( InFile ); 
      switch (InChar) { 
      case '0': putpixel(j,i, 0); break; 
      case '1': putpixel(j,i, 1); break; 
      case '2': putpixel(j,i, 2); break; 
      case '3': putpixel(j,i, 3); break; 
      case '4': putpixel(j,i, 4); break; 
      case '5': putpixel(j,i, 5); break; 
      case '6': putpixel(j,i, 6); break; 
      case '7': putpixel(j,i, 7); break; 
      case '8': putpixel(j,i, 8); break; 
      case '9': putpixel(j,i, 9); break; 
      case 'A': putpixel(j,i,10); break; 
      case 'B': putpixel(j,i,11); break; 
      case 'C': putpixel(j,i,12); break; 
      case 'D': putpixel(j,i,13); break; 
      case 'E': putpixel(j,i,14); break; 
      default : putpixel(j,i,15); 
      } 
    } 
  } 
  fclose(InFile); 
} 
 
void far RestoreState() { 
  FILE *InFile; 
  int i,j,k; 
 
  InFile = fopen("SAVESTAT.DTA","rb"); 
 
// Card Deck 
 
  for (i=0;i<DECK_SIZE;i++) { 
    fgets(gS,80,InFile); 
    gCard[i].Shuffle[0] = gS[0]; 
    gCard[i].Shuffle[1] = gS[1]; 
    gCard[i].Shuffle[2] = gS[2]; 
    gCard[i].Shuffle[3] = gS[3]; 
    gCard[i].Title[0] = gS[4]; 
    gCard[i].Title[1] = gS[5]; 
    gCard[i].Title[2] = gS[6]; 
    gCard[i].Rank = gS[7]; 
    gCard[i].Suit = gS[8]; 
    gS[0] = gS[9]; 
    gS[1] = gS[10]; 
    gS[2] = gS[11]; 
    gS[3] = 0x00; 
    gCard[i].Value = atoi(gS); 
    if (gS[12] == 'T') 
         gCard[i].IsWild = true; 
    else gCard[i].IsWild = false; 
  } 
 
// Hands 
 
  for (i=0;i<NUM_PLAYERS;i++) { 
    for (j=0;j<DECK_SIZE;j++) { 
      fgets(gS,80,InFile); 
      gHand[i][j].Rank = gS[0]; 
      gS[0] = gS[1]; 
      gS[1] = gS[2]; 
      gS[2] = gS[3]; 
      gS[3] = 0x00; 
      gHand[i][j].Index = atoi(gS); 
      if (gS[4] == 'T') 
           gHand[i][j].Selected = true; 
      else gHand[i][j].Selected = false; 
    } 
  } 
 
// Top Discard Pile 
 
  fgets(gS,80,InFile); 
  gS[3] = 0x00; 
  gTopPile = atoi(gS); 
 
// Stock 
 
  for (i=0;i<DECK_SIZE;i++) { 
    fgets(gS,80,InFile); 
    gS[3] = 0x00; 
    gStock[i] = atoi(gS); 
  } 
 
// Discard Pile 
 
  for (i=0;i<DECK_SIZE;i++) { 
    fgets(gS,80,InFile); 
    gS[3] = 0x00; 
    gDiscard[i] = atoi(gS); 
  } 
 
// Melds and Red Trey 
 
  for (i=0;i<NUM_SIDES;i++) { 
    for (j=0;j<MELD_LOCATIONS;j++) { 
      fgets(gS,80,InFile); 
      if (gS[0] == 'T') 
           gMeld[i][j].IsBook = true; 
      else gMeld[i][j].IsBook = false; 
      if (gS[1] == 'T') 
           gMeld[i][j].HasWild = true; 
      else gMeld[i][j].HasWild = false; 
      for (k=0;k<MELD_DEPTH;k++) { 
        gS[0] = gS[(k*3)+2]; 
        gS[1] = gS[(k*3)+3]; 
        gS[2] = gS[(k*3)+4]; 
        gS[3] = 0x00; 
        gMeld[i][j].Position[k] = atoi(gS); 
      } 
    } 
  } 
 
// Score 
 
  for (i=0;i<MAX_ROUNDS;i++) { 
    fgets(gS,80,InFile); 
    gS[60] = gS[5]; 
    gS[61] = gS[6]; 
    gS[62] = gS[7]; 
    gS[63] = gS[8]; 
    gS[64] = gS[9]; 
    gS[5] = 0x00; 
    gBonusPoints[i][0] = atoi(gS); 
    gS[0] = gS[60]; 
    gS[1] = gS[61]; 
    gS[2] = gS[62]; 
    gS[3] = gS[63]; 
    gS[4] = gS[64]; 
    gS[5] = 0x00; 
    gBonusPoints[i][1] = atoi(gS); 
    fgets(gS,80,InFile); 
    gS[60] = gS[5]; 
    gS[61] = gS[6]; 
    gS[62] = gS[7]; 
    gS[63] = gS[8]; 
    gS[64] = gS[9]; 
    gS[5] = 0x00; 
    gMeldPoints[i][0] = atoi(gS); 
    gS[0] = gS[60]; 
    gS[1] = gS[61]; 
    gS[2] = gS[62]; 
    gS[3] = gS[63]; 
    gS[4] = gS[64]; 
    gS[5] = 0x00; 
    gMeldPoints[i][1] = atoi(gS); 
    fgets(gS,80,InFile); 
    gS[60] = gS[5]; 
    gS[61] = gS[6]; 
    gS[62] = gS[7]; 
    gS[63] = gS[8]; 
    gS[64] = gS[9]; 
    gS[5] = 0x00; 
    gScore[i][0] = atoi(gS); 
    gS[0] = gS[60]; 
    gS[1] = gS[61]; 
    gS[2] = gS[62]; 
    gS[3] = gS[63]; 
    gS[4] = gS[64]; 
    gS[5] = 0x00; 
    gScore[i][1] = atoi(gS); 
  } 
 
// Miscellaneous 
 
  fgets(gS,80,InFile); 
  if (gS[0] == 'T') 
       gMeldedBefore[NS_SIDE] = true; 
  else gMeldedBefore[NS_SIDE] = false; 
  if (gS[1] == 'T') 
       gMeldedBefore[EW_SIDE] = true; 
  else gMeldedBefore[EW_SIDE] = false; 
  gS[0] = gS[2]; 
  gS[1] = gS[3]; 
  gS[2] = gS[4]; 
  gS[3] = 0x00; 
  gNextCardInStock = atoi(gS); 
  gS[0] = gS[5]; 
  gS[1] = gS[6]; 
  gS[2] = gS[7]; 
  gS[3] = 0x00; 
  gRounds = atoi(gS); 
 
// Set Active Player 
 
  fgets(gS,80,InFile); 
  switch (gS[0]) { 
  case '0': 
    gActPlayer = NORTH_P; 
    gActSide   = NS_SIDE; 
    break; 
  case '1': 
    gActPlayer = EAST_P; 
    gActSide   = EW_SIDE; 
    break; 
  case '2': 
    gActPlayer = SOUTH_P; 
    gActSide   = NS_SIDE; 
    break; 
  case '3': 
    gActPlayer = WEST_P; 
    gActSide   = EW_SIDE; 
    break; 
  } 
 
  fclose(InFile); 
  Refresh(); 
  Gprintf(1,1,YELLOW,BLACK, " STATE OF GAME RESORED "); 
} 
 
void far SaveBehindWindow(char *FileName, int Top, int Left, 
          int Bottom, int Right) { 
  int i, j, ColorBuffer; 
  int PixelTop    = Top*gTextHeight; 
  int PixelLeft   = Left*gTextWidth; 
  int PixelBottom = ((Bottom+1)*gTextHeight)-1; 
  int PixelRight  = ((Right+1)*gTextWidth)-1; 
  FILE *OutFile; 
  char OutChar=' '; 
 
  i=j=ColorBuffer=0; 
  OutFile = fopen(FileName, "wb"); 
  for (i=PixelTop;i<=PixelBottom;i++) { 
    for (j=PixelLeft;j<=PixelRight;j++) { 
      ColorBuffer = getpixel(j,i); 
      switch (ColorBuffer) { 
      case  0: OutChar = '0'; break; 
      case  1: OutChar = '1'; break; 
      case  2: OutChar = '2'; break; 
      case  3: OutChar = '3'; break; 
      case  4: OutChar = '4'; break; 
      case  5: OutChar = '5'; break; 
      case  6: OutChar = '6'; break; 
      case  7: OutChar = '7'; break; 
      case  8: OutChar = '8'; break; 
      case  9: OutChar = '9'; break; 
      case 10: OutChar = 'A'; break; 
      case 11: OutChar = 'B'; break; 
      case 12: OutChar = 'C'; break; 
      case 13: OutChar = 'D'; break; 
      case 14: OutChar = 'E'; break; 
      default: OutChar = 'F'; 
      } 
      fputc( OutChar, OutFile ); 
    } 
  } 
  fclose(OutFile); 
} 
 
void far SaveState() { 
  FILE *OutFile; 
  int i,j,k; 
 
  OutFile = fopen("SAVESTAT.DTA","wb"); 
 
// Card Deck 
 
  for (i=0;i<DECK_SIZE;i++) { 
    fprintf(OutFile,"%c",gCard[i].Shuffle[0]); 
    fprintf(OutFile,"%c",gCard[i].Shuffle[1]); 
    fprintf(OutFile,"%c",gCard[i].Shuffle[2]); 
    fprintf(OutFile,"%c",gCard[i].Shuffle[3]); 
    fprintf(OutFile,"%c",gCard[i].Title[0]); 
    fprintf(OutFile,"%c",gCard[i].Title[1]); 
    fprintf(OutFile,"%c",gCard[i].Title[2]); 
    fprintf(OutFile,"%c",gCard[i].Rank); 
    fprintf(OutFile,"%c",gCard[i].Suit); 
    fprintf(OutFile,"%3.1d",gCard[i].Value); 
    if (gCard[i].IsWild) 
         fprintf(OutFile,"T\r\n"); 
    else fprintf(OutFile,"F\r\n"); 
  } 
 
// Hands 
 
  for (i=0;i<NUM_PLAYERS;i++) { 
    for (j=0;j<DECK_SIZE;j++) { 
      fprintf(OutFile,"%c",gHand[i][j].Rank); 
      fprintf(OutFile,"%3.1d",gHand[i][j].Index); 
      if (gHand[i][j].Selected) 
           fprintf(OutFile,"T\r\n"); 
      else fprintf(OutFile,"F\r\n"); 
    } 
  } 
 
// Top Discard Pile 
 
  fprintf(OutFile,"%3.1d\r\n",gTopPile); 
 
// Stock 
 
  for (i=0;i<DECK_SIZE;i++) 
    fprintf(OutFile,"%3.1d\r\n",gStock[i]); 
 
// Discard Pile 
 
  for (i=0;i<DECK_SIZE;i++) 
    fprintf(OutFile,"%3.1d\r\n",gDiscard[i]); 
 
// Melds and Red Trey 
 
  for (i=0;i<NUM_SIDES;i++) { 
    for (j=0;j<MELD_LOCATIONS;j++) { 
      if (gMeld[i][j].IsBook) 
           fprintf(OutFile,"T"); 
      else fprintf(OutFile,"F"); 
      if (gMeld[i][j].HasWild) 
           fprintf(OutFile,"T"); 
      else fprintf(OutFile,"F"); 
      for (k=0;k<MELD_DEPTH;k++) 
        fprintf(OutFile,"%3.1d",gMeld[i][j].Position[k]); 
      fprintf(OutFile,"\r\n"); 
    } 
  } 
 
// Score 
 
  for (i=0;i<MAX_ROUNDS;i++) { 
    for (j=0;j<NUM_SIDES;j++) { 
      fprintf(OutFile,"%5.1d",gBonusPoints[i][j]); 
    } 
    fprintf(OutFile,"\r\n"); 
    for (j=0;j<NUM_SIDES;j++) { 
      fprintf(OutFile,"%5.1d",gMeldPoints[i][j]); 
    } 
    fprintf(OutFile,"\r\n"); 
    for (j=0;j<NUM_SIDES;j++) { 
      fprintf(OutFile,"%5.1d",gScore[i][j]); 
    } 
    fprintf(OutFile,"\r\n"); 
  } 
 
// Miscellaneous 
 
  if (gMeldedBefore[NS_SIDE]) 
       fprintf(OutFile,"T"); 
  else fprintf(OutFile,"F"); 
  if (gMeldedBefore[EW_SIDE]) 
       fprintf(OutFile,"T"); 
  else fprintf(OutFile,"F"); 
  fprintf(OutFile,"%3.1d",gNextCardInStock); 
  fprintf(OutFile,"%3.1d\r\n",gRounds); 
 
// Save who is active player 
 
  switch (gActPlayer) { 
  case NORTH_P: 
    fprintf(OutFile,"%c\r\n",'0'); 
    break; 
  case EAST_P: 
    fprintf(OutFile,"%c\r\n",'1'); 
    break; 
  case SOUTH_P: 
    fprintf(OutFile,"%c\r\n",'2'); 
    break; 
  case WEST_P: 
    fprintf(OutFile,"%c\r\n",'3'); 
    break; 
  } 
 
  fclose(OutFile); 
  Gprintf(1,1,YELLOW,BLACK, " STATE OF GAME SAVED "); 
} 
 
int far SelectCardInHand(int Who, char a) { 
  int i,b; 
 
  i=b=0; 
  for (;i<DECK_SIZE;i++) { 
    b = gHand[Who][i].Index; 
    if (b != EMPTY) { 
      if (gCard[b].Title[0] == a) { 
        if (!(gHand[Who][i].Selected)) { 
          gHand[Who][i].Selected = true; 
          return i; 
        } 
      } 
    } 
  } 
 
  return EMPTY; 
} 
 
void far ShowMelds(int Who, int Row) { 
  int i,j,a; 
 
  i=j=a=0; 
  gCanastaCount[Who] = 0; 
  for (i=0;i<MELD_LOCATIONS;i++) { 
    gMeld[Who][i].IsBook = false; 
    gMeld[Who][i].HasWild = false; 
    for (j=0;j<MELD_DEPTH;j++) { 
      a = gMeld[Who][i].Position[j]; 
      if (a == EMPTY) break; 
      if (gCard[a].IsWild) gMeld[Who][i].HasWild = true; 
    } 
    if (j>=7) gMeld[Who][i].IsBook = true; 
  } 
  for (i=MELD_LOCATIONS-1;i>=1;i--) { 
    if (gMeld[Who][i].IsBook) { 
      if (gMeld[Who][i].HasWild) { 
 
// Black canasta 
 
        for (j=0;j<MELD_DEPTH;j++) { 
          a = gMeld[Who][i].Position[j]; 
          if (gCard[a].IsWild) { 
            DisplayCard(a,Row+4, 
              i*MELD_DISPLAY_WIDTH+MELD_DISPLAY_MARGIN, false); 
            break; 
          } 
        } 
        for (j=0;j<MELD_DEPTH;j++) { 
          a = gMeld[Who][i].Position[j]; 
          if (!(gCard[a].IsWild)) { 
            DisplayCard(a,Row+5, 
              i*MELD_DISPLAY_WIDTH+MELD_DISPLAY_MARGIN, false); 
            break; 
          } 
        } 
      } 
      else { 
 
// Red canasta 
 
        for (j=0;j<MELD_DEPTH;j++) { 
          a = gMeld[Who][i].Position[j]; 
          if (!(gCard[a].IsWild)) { 
            if ((gCard[a].Suit == 'H') || (gCard[a].Suit == 'D')) { 
              DisplayCard(a,Row+5, 
                i*MELD_DISPLAY_WIDTH+MELD_DISPLAY_MARGIN, false); 
              break; 
            } 
          } 
        } 
      } 
      GetPixelsFromFile("DECKSIDE.PXL",Row+5, 
        (i*MELD_DISPLAY_WIDTH+MELD_DISPLAY_MARGIN)-1, false ); 
      gCanastaCount[Who]++; 
    } 
    else { 
 
// Non-canasta 
 
      for (j=0;j<6;j++) { 
        if (gMeld[Who][i].Position[j] == EMPTY) break; 
        DisplayCard(gMeld[Who][i].Position[j], j+Row, 
          i*MELD_DISPLAY_WIDTH+MELD_DISPLAY_MARGIN, false ); 
      } 
    } 
  } 
  for (j=0;j<8;j++) { 
 
// Threes 
 
    if (gMeld[Who][0].Position[j] != EMPTY) { 
      DisplayCard(gMeld[Who][0].Position[j], j+Row, 
        MELD_DISPLAY_MARGIN, false ); 
    } 
  } 
} 
 
void far ShowScore() { 
  int i; 
 
  Gprintf(STOCK_ROW-1, 7,YELLOW,BLACK,  "        We | They"); 
  if (gRounds<=1) { 
    Gprintf(STOCK_ROW,   7,YELLOW,BLACK,"B:         |"); 
    Gprintf(STOCK_ROW+1, 7,YELLOW,BLACK,"M:         |"); 
    Gprintf(STOCK_ROW+2, 7,YELLOW,BLACK,"  ---------|---------"); 
    Gprintf(STOCK_ROW+3, 7,YELLOW,BLACK,"T:         |"); 
  } else { 
    for (i=1;i<gRounds;i++) { 
      Gprintf(STOCK_ROW+(i*4)-4, 7,YELLOW,BLACK,"B:"); 
      Gprintf(STOCK_ROW+(i*4)-4, 9,YELLOW,BLACK,"%9.1d",  gBonusPoints[i-1][NS_SIDE]); 
      Gprintf(STOCK_ROW+(i*4)-4,18,YELLOW,BLACK,"|%9.1d", gBonusPoints[i-1][EW_SIDE]); 
      Gprintf(STOCK_ROW+(i*4)-3, 7,YELLOW,BLACK,"M:"); 
      Gprintf(STOCK_ROW+(i*4)-3, 9,YELLOW,BLACK,"%9.1d",  gMeldPoints[i-1][NS_SIDE]); 
      Gprintf(STOCK_ROW+(i*4)-3,18,YELLOW,BLACK,"|%9.1d", gMeldPoints[i-1][EW_SIDE]); 
      Gprintf(STOCK_ROW+(i*4)-2, 7,YELLOW,BLACK,"  ---------|---------"); 
      Gprintf(STOCK_ROW+(i*4)-1, 7,YELLOW,BLACK,"T:"); 
      Gprintf(STOCK_ROW+(i*4)-1, 9,YELLOW,BLACK,"%9.1d",  gScore[i-1][NS_SIDE]); 
      Gprintf(STOCK_ROW+(i*4)-1,18,YELLOW,BLACK,"|%9.1d", gScore[i-1][EW_SIDE]); 
    } 
  } 
} 
 
void far ShowMenu(cMenu *PullDown, int Entries) { 
  int i=0; 
  int MenuWidth = strlen(PullDown[0].caption); 
  int Top       = PullDown[0].row1-1; 
  int Left      = PullDown[0].col1-1; 
  int Bottom    = PullDown[Entries-1].row1+1; 
  int Right     = PullDown[Entries-1].col1+MenuWidth; 
 
  SaveBehindWindow("MENUBACK.DTA", Top, Left, Bottom +1, Right +1); 
  Gprintf(Top, Left, BLACK, WHITE, "Ú"); 
  for (i=0;i<MenuWidth;i++ ) 
    Gprintf(Top, PullDown[0].col1+i, BLACK, WHITE, "Ä"); 
  Gprintf(Top, PullDown[0].col1+MenuWidth, BLACK, WHITE, "¿"); 
  for (i=0;i<Entries;i++) { 
    Gprintf(PullDown[i].row1, PullDown[i].col1-1, BLACK, WHITE, "³"); 
    Gprintf(PullDown[i].row1, PullDown[i].col1, BLACK, WHITE, 
      "%*.*s", MenuWidth, MenuWidth, PullDown[i].caption); 
    Gprintf(PullDown[i].row1, PullDown[i].col1+MenuWidth, 
      BLACK, WHITE, "³%c",0xB2); 
    Gprintf(PullDown[i].row1, PullDown[i].col1+1, 
      RED, WHITE, "%c", PullDown[i].caption[1]); 
  } 
  Gprintf(Bottom , Left, BLACK, WHITE, "À"); 
  for (i=1;i<=MenuWidth;i++ ) 
    Gprintf(Bottom , Left+i, BLACK, WHITE, "Ä"); 
  Gprintf(Bottom , Right, BLACK, WHITE, "Ù%c",0xB2); 
  for (i=1;i<=MenuWidth+2;i++ ) 
    Gprintf(Bottom +1, Left+i, BLACK, WHITE, "%c",0xB2); 
} 
 
void far ShuffleDeck() { 
  int i; 
 
  for (i=0;i<DECK_SIZE;i++) { 
    sprintf(gRecord[i]  ,"%3.3s",gCard[i].Shuffle); 
    sprintf(gRecord[i]+3,"%2.2s",gCard[i].Title); 
    sprintf(gRecord[i]+5,"%c",gCard[i].Rank); 
    sprintf(gRecord[i]+6,"%c",gCard[i].Suit); 
    sprintf(gRecord[i]+7,"%2d",gCard[i].Value); 
    if (gCard[i].IsWild) 
         sprintf(gRecord[i]+9,"T"); 
    else sprintf(gRecord[i]+9,"F"); 
    gRecord[i][10] = 0x00; 
  } 
 
  qsort((void *)gRecord, DECK_SIZE, sizeof(gRecord[0]), sf); 
 
  for (i=0;i<DECK_SIZE;i++) { 
    gCard[i].Shuffle[0] = gRecord[i][0]; 
    gCard[i].Shuffle[1] = gRecord[i][1]; 
    gCard[i].Shuffle[2] = gRecord[i][2]; 
    gCard[i].Title[0] = gRecord[i][3]; 
    gCard[i].Title[1] = gRecord[i][4]; 
    gCard[i].Rank = gRecord[i][5]; 
    gCard[i].Suit = gRecord[i][6]; 
    if (gRecord[i][9] == 'T') 
         gCard[i].IsWild = true; 
    else gCard[i].IsWild = false; 
    if (gRecord[i][7] == ' ') gS[0] = '0'; else gS[0] = gRecord[i][7]; 
    if (gRecord[i][8] == ' ') gS[1] = '0'; else gS[1] = gRecord[i][8]; 
    gS[2] = 0x00; 
    gCard[i].Value = atoi(gS); 
  } 
} 
 
void far SortHand(int Who) { 
  int i; 
 
  for (i=0;i<DECK_SIZE;i++) { 
    sprintf(gRecord[i],"%c",gHand[Who][i].Rank); 
    if (gHand[Who][i].Index == EMPTY) 
         sprintf(gRecord[i]+1,"999"); 
    else sprintf(gRecord[i]+1,"%3d",gHand[Who][i].Index); 
    if (gHand[Who][i].Selected) 
         sprintf(gRecord[i]+4,"T"); 
    else sprintf(gRecord[i]+4,"F"); 
    gRecord[i][5] = 0x00; 
  } 
 
  qsort((void *)gRecord, DECK_SIZE, sizeof(gRecord[0]), sf); 
 
  for (i=0;i<DECK_SIZE;i++) { 
    gHand[Who][i].Rank = gRecord[i][0]; 
    if (gRecord[i][4] == 'T') 
         gHand[Who][i].Selected = true; 
    else gHand[Who][i].Selected = false; 
    if (gRecord[i][1] == ' ') gS[0] = '0'; else gS[0] = gRecord[i][1]; 
    if (gRecord[i][2] == ' ') gS[1] = '0'; else gS[1] = gRecord[i][2]; 
    if (gRecord[i][3] == ' ') gS[2] = '0'; else gS[2] = gRecord[i][3]; 
    gS[3] = 0x00; 
    gHand[Who][i].Index = atoi(gS); 
    if (gHand[Who][i].Index == 999) gHand[Who][i].Index = EMPTY; 
  } 
} 
 
void far StartOver() { 
  int i,j,k; 
 
  // Reset global variables 
 
  gDealer += 1; 
  gDealer %= NUM_PLAYERS; 
  gActSide = gActPlayer = gDealer; 
  gActSide %= NUM_SIDES; 
  NextCardBack(); 
  gNextCardInStock = DECK_SIZE-1; 
  gTopPile = k = EMPTY; 
  gEndRound = false; 
  gChanged = true; 
  gPhase = 0; 
// 08Nov2010 Next two lines added 
  for (i=0;i<NUM_SIDES;i++) { 
    gMeldedBefore[i] = false; 
  } 
 
  // Create Card Deck. 
 
  for (i=0; i<DECK_SIZE-4; i++ ) { 
    j = i % 13; 
    itoa(rand() % RAND_MAX,gCard[i].Shuffle,36); 
    gCard[i].Title[0] = gRankString[j]; 
    gCard[i].Rank = 'a'+(13-j); 
    if (j == 0) { 
      k++; 
      k %= 4; 
    } 
    gCard[i].Title[1] = gSuitString[k]; 
    gCard[i].Title[2] = 0x00; 
    gCard[i].Suit = gSuitString[k]; 
    switch (gCard[i].Title[0]) { 
    case '3': case '4': case '5': case '6': case '7': 
      gCard[i].Value = 5; 
      gCard[i].IsWild = false; 
      break; 
    case '8': case '9': case 'T': case 'J': case 'Q': case 'K': 
      gCard[i].Value = 10; 
      gCard[i].IsWild = false; 
      break; 
    case 'A': 
      gCard[i].Value = 20; 
      gCard[i].IsWild = false; 
      break; 
    case '2': 
      gCard[i].Value = 20; 
      gCard[i].IsWild = true; 
      break; 
    } 
  } 
 
  // Add jokers 
 
  for (; i<DECK_SIZE; i++ ) { 
    itoa(rand() % RAND_MAX,gCard[i].Shuffle,36); 
    gCard[i].Title[0] = 'Z'; 
    if ((i%2) == 0) 
      gCard[i].Title[1] = '1'; 
    else 
      gCard[i].Title[1] = '2'; 
    gCard[i].Title[2] = 0x00; 
    gCard[i].Rank = 'a'; 
    gCard[i].Suit = '*'; 
    gCard[i].Value = 50; 
    gCard[i].IsWild = true; 
  } 
 
  ShuffleDeck(); 
 
  // Clear the Table. 
 
  for (i=0;i<NUM_SIDES;i++) { 
    for (j=0;j<MELD_LOCATIONS;j++) { 
      gMeld[i][j].IsBook = false; 
      gMeld[i][j].HasWild = false; 
      for (k=0;k<MELD_DEPTH;k++) { 
        gMeld[i][j].Position[k] = EMPTY; 
      } 
    } 
  } 
  for (i=0;i<DECK_SIZE;i++) { 
    gStock[i] = i; 
    gDiscard[i] = EMPTY; 
    for (j=0;j<NUM_PLAYERS;j++) { 
      gHand[j][i].Index = EMPTY; 
      gHand[j][i].Rank = '~'; 
      gHand[j][i].Selected = false; 
    } 
  } 
 
  // Deal 
 
  for (i=0;i<CARDS_TO_DEAL;i++) { 
    for (j=0;j<NUM_PLAYERS;j++) { 
      gHand[j][i].Index = DrawCard(j); 
      gHand[j][i].Rank = gCard[gHand[j][i].Index].Rank; 
    } 
  } 
  SortHand(NORTH_P); 
  SortHand(EAST_P); 
  SortHand(SOUTH_P); 
  SortHand(WEST_P); 
 
  // Turn up first upcard from stock 
 
  gTopPile++; 
  gDiscard[gTopPile] = gStock[gNextCardInStock]; 
  gStock[gNextCardInStock] = EMPTY; 
  gNextCardInStock--; 
} 
 
bool far TakeDiscardPile() { 
  int i,d; 
  char a,b; 
 
  i=d=0; 
  a=b=' '; 
  if (!(gMeldedBefore[gActSide])) return false; 
  if (gTopPile == EMPTY) return false; 
  b = gCard[gDiscard[gTopPile]].Title[0]; 
 
  switch (b) { 
  case 'Z': 
  case '2': 
  case '3': 
    return false; 
  } 
  a = MeldCards(true); 
  if (a == ' ') return false; 
  if (!(MinLegalMeld(true))) return false; 
  if (a == b) { 
    for (i=0;i<DECK_SIZE;i++) { 
      if (gHand[gActPlayer][i].Index == EMPTY) { 
        break; 
      } 
    } 
    for (;;) { 
      d = gDiscard[gTopPile]; 
      gDiscard[gTopPile] = EMPTY; 
      gTopPile--; 
      gHand[gActPlayer][i].Index = d; 
      gHand[gActPlayer][i].Rank = gCard[d].Rank; 
      gHand[gActPlayer][i].Selected = false; 
      gHandCardCount[gActPlayer]++; 
      if (gTopPile == EMPTY) break; 
      i++; 
    } 
    SortHand(gActPlayer); 
  } 
  else { 
    PlayerDraw(); 
    return true; 
  } 
  return true; 
} 
 
void far WaitASec() { 
  time_t t, tSave; 
 
  t = time( NULL ); 
  tSave = t + 1.75; 
  while ( tSave > t ) t = time( NULL ); 
} 
 
void far ProgramConstructor() { 
  int i,j,GraphError; 
  int GraphDevice = VGA; 
  int GraphMode = VGAHI; 
 
  i=j=GraphError=0; 
  putenv("TZ=PST8PDT"); 
  tzset(); 
 
  initgraph( &GraphDevice, &GraphMode, PATH_TO_BGI ); 
  GraphError = graphresult(); 
  if( GraphError != grOk ){ 
    pd2(); 
    printf("Path to BGI files: \"%s\".\n", PATH_TO_BGI ); 
    printf("Graphics error in %s:\n", PROGNAME); 
    printf("%s\nPress a key to continue...\n", 
      grapherrormsg( GraphError ) ); 
    getch(); 
    exit( 1 ); 
  } 
  settextstyle(DEFAULT_FONT, HORIZ_DIR, 1); 
  gTextHeight = textheight( "H" ); 
  gTextWidth = textwidth( "M" ); 
 
  srand((unsigned) time(NULL)); 
 
  for (i=0;i<MAX_ROUNDS;i++) { 
    for (j=0;j<NUM_SIDES;j++) { 
      gBonusPoints[i][j] = 0; 
      gMeldPoints[i][j]  = 0; 
      gScore[i][j]       = 0; 
    } 
  } 
  StartOver(); 
} 
 
bool far MainLoop() { 
  char Answer[3] = "  "; 
 
  if (gChanged) Refresh(); 
  gChanged = false; 
  if (gEndRound) { 
    FigureScore(gRounds-1); 
    Gprintf( 0, 1, BLACK, WHITE, " End of Round               "); 
    Gprintf( 1, 1, BLACK, WHITE, " Press a key to continue... "); 
    gRounds++; 
    ShowScore(); 
    getch(); 
    if (gEndGame) { 
      cleardevice(); 
      Gprintf( 0, 1, BLACK, WHITE, " End of Game!               "); 
      Gprintf( 1, 1, BLACK, WHITE, " Press a key to continue... "); 
      ShowScore(); 
      getch(); 
      return false; 
    } 
    StartOver(); 
    Refresh(); 
    Gprintf( 1, 1, BLACK, WHITE, " New Round                  "); 
  } 
  Answer[0] = ReadDesktop(); 
  switch (Answer[0]) { 
  case 0x1B: // Esc 
  case 'e': // Exit 
    ProgramDestructor(); 
    exit( 7 ); 
    break; 
  case 'h': // Help 
    Answer[1] = ReadMenu(gHelpMenu,HELP_PULLDOWN_COUNT); 
    if (Answer[1] == 'a') AboutThisProgram(); 
    gChanged = true; 
    break; 
  default: 
    switch (gPhase) { 
    case 0: 
      switch (Answer[0]) { 
      case 't': // Take 
        if (TakeDiscardPile()) gPhase = 1; 
        /* Failure to take repeats Phase 0 */ 
        gChanged = true; 
        break; 
      case 'd': // Draw 
        if (PlayerDraw()) gPhase = 1; 
        /* Failure to draw repeats Phase 0 */ 
        gChanged = true; 
        break; 
      case 'r': // Restore 
        RestoreState(); 
        break; 
      case 's': // Save 
        SaveState(); 
        break; 
      } 
      break; 
    case 1: 
      switch (Answer[0]) { 
      case 'm': // Meld 
        MeldCards(false); 
        gChanged = true; 
        break; 
      case 'd': // Discard 
        if (Discard()) { 
          switch (gActPlayer) { 
          case NORTH_P: 
            gActPlayer = EAST_P; 
            gActSide   = EW_SIDE; 
            break; 
          case EAST_P: 
            gActPlayer = SOUTH_P; 
            gActSide   = NS_SIDE; 
            break; 
          case SOUTH_P: 
            gActPlayer = WEST_P; 
            gActSide   = EW_SIDE; 
            break; 
          case WEST_P: 
            gActPlayer = NORTH_P; 
            gActSide   = NS_SIDE; 
            break; 
          } 
          gPhase = 0; 
        } 
        gChanged = true; 
        break; 
      } 
      break; 
    } 
  } 
 
  return true; 
} 
 
void far ProgramDestructor() { 
  closegraph(); 
  pd2(); 
} 
 
void far pd2() { 
  textmode( C4350 ); 
  textcolor( LIGHTGRAY ); 
  textbackground( BLACK ); 
  clrscr(); 
} 
 
int far sf( const void *a, const void *b) { 
   return( strcmp((char *)a,(char *)b) ); 
} 
 
// EOF: PLAY2CAN.CPP


```

---

### Post by schauerlich on 2011-07-19
You came here asking for help. We told you we can't help you, because you're using horribly outdated tools and programming in an unmanageable style. When we say we can't do much until you address those two issues, you say "I've been programming for 35 years so I know better."

What were you expecting to happen?

---

### Post by worseisworser on 2011-07-19
> **machdohvah said:**
> There are two problems with g++ that I have had in the past. One, I am not able to stop the action like a can with getch() supported by conio.h, and I have never been successful in finding a function that allows me to place a pixel color in a window.

There are certain things and certain problems you should not ignore or simply compromise against, and you have just found two of them. What you're looking for is most likely a library called *ncurses*, or something similar to it at least.

You'll need the ncurses development libraries and the documentation to get started:

```

$ aptitude search ncurses
...
...

$ sudo aptitude install libncurses-dev ncurses-doc
...
...

```


...hm... where did it actually install the docs? Let's see if there is some HTML docs included with the package:

```

$ dpkg -L ncurses-doc | grep html
...
...

```

Indeed there it is, open your browser somewhere around   *file:///usr/share/doc/ncurses-doc/html/index.html*   ..this should get you started.

PS: Even though this is not conio.h & Co., note how a function with a somewhat familiar name now exists on your system:

```

$ man -k getch

getch (3ncurses)     - get (or push back) characters from curses terminal keyboard
getchar (3)          - input of characters and strings
getchar (3posix)     - get a byte from a stdin stream
getchar_unlocked (3) - nonlocking stdio functions
getchar_unlocked (3posix) - stdio with explicit client locking
mvgetch (3ncurses)   - get (or push back) characters from curses terminal keyboard
mvwgetch (3ncurses)  - get (or push back) characters from curses terminal keyboard
ungetch (3ncurses)   - get (or push back) characters from curses terminal keyboard
ungetch_sp (3ncurses) - curses screen-pointer extension
wgetch (3ncurses)    - get (or push back) characters from curses terminal keyboard

```

Every function is documented well:

```

$ man 3ncurses getch

```


Hit the 'q' key to exit the man-page browser.

---

### Post by machdohvah on 2011-07-20
> **schauerlich said:**
> You came here asking for help. We told you we can't help you, because you're using horribly outdated tools and programming in an unmanageable style. When we say we can't do much until you address those two issues, you say "I've been programming for 35 years so I know better."

What were you expecting to happen?
 
I agree. I erased GCANASTA.CPP and PLAY2CAN.CPP in favor of PLAY4CAN.CPP. As far as converting this thing to a g++ code and using the libraries as suggested by the next post not quoted here. I still would be in the dark about every other function and objects available. What I would like to see is an interface with extensively interactive help files for each function, keyword, and objects that are included in any given library. Several candidates came close with extensive library help files, but nothing ever came close to Borland's help file system. They were awesome.

Therefore, I declare this thread closed and SOLVED. I will be content with my tiny DOS emulator and re-writing the four player version in round robin fashion. If anyone is upset that I attempted to solve the AI portion here, just know that in 25 years from now when everything is holographic, you will feel nostalgic for the days when there was something called a flat screen.

---

### Post by unknownPoster on 2011-07-20
> **machdohvah said:**
> If anyone is upset that I attempted to solve the AI portion here, just know that in 25 years from now when everything is holographic, you will feel nostalgic for the days when there was something called a flat screen.

Not sure what that has to do with anything at all.

All of us offered very similar advice, yet you chose to ignore most of it. What else do you expect us to do?

---

### Post by schauerlich on 2011-07-20
> **machdohvah said:**
> Therefore, I declare this thread closed and SOLVED. I will be content with my tiny DOS emulator and re-writing the four player version in round robin fashion. If anyone is upset that I attempted to solve the AI portion here, just know that in 25 years from now when everything is holographic, you will feel nostalgic for the days when there was something called a flat screen.

No skin off my back.

---

### Post by worseisworser on 2011-07-20
> **machdohvah said:**
>  I still would be in the dark about every other function and objects available. What I would like to see is an interface with extensively interactive help files for each function, keyword, and objects that are included in any given library. 


Oookkeee, riiiight. :rolleyes: Did you just tell me to go **** myself? How quaint, but well, giddaut. The door is that way -->

... don't let it hit you on your way out.

---

### Post by slavik on 2011-07-20
I dislike babysitting.

---

