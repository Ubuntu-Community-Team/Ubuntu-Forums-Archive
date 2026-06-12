---
title: "[C++] Random number problem."
date: 2010-06-03
forum: Programming Talk
---

### Post by YourMomsASmurph on 2010-06-03
So problem isn't solved, the original post in this thread was. Figured this was better idea than making a new thread... (Will make a new thread when this dies -- If I dont get a response.)

Search for **99 to find the problem.
(Havent spent any time looking at it yet, heading to bed. If it just a simple logic defect then say so, and ill try to find it myself tomorrow.)
[PHP]
/*

**0
----
you can't search this.
-> If needed, set this up so that it uses 7 decks
vector pushback randomcard 7*52.


**1
-----
Replace int with double, and limit to 2 decimal places.

**2
-----
Add in cout message that prints the total value of the cards for players and 
the dealer.

**2.1
------
Add in insurance option // Hide second dealer card.

**99
-----
Need to find out why my search doesnt find and change the value of the ace.
    As of right now if I have A 5 10 -- the value adds up to 26 in stead of 16.

*/

#include <cstdlib>
#include <iostream>
#include <vector>
#include <string>
#include <cstring>


using namespace std;



//Card Structure
struct card { //card stucture
    char suit; // suit
    char face; // face value (AKQJ 10 9 8 ...)
    int worth;// value of card A=11, KQJ10=10, 9=9, etc.)
        
    void random();
};
//Random Card Generator.
void card::random() { // definition for card::random()

    int rndnum(0);
    
    rndnum = ((rand() % 4) + 1); //random card 1-4
    
    switch (rndnum) { // puts'A'suit depending on the random card between 1-4 default case is the error case.
        
        case 1:
            suit = 'S';
            break;
        case 2:
            suit = 'H';
            break;
        case 3:
            suit = 'C';
            break;
        case 4:
            suit = 'D';
            break;
        default:
            suit = 'E';
            break;
    }
    
    rndnum = ((rand() % 13) + 1); //random card 1-13
    
    switch (rndnum) { // random card between 1 and 13 is selected, this will give it the face value, and worth. 1=A, 2=2, ..., 10=10, 11=J... ) default case is the error case.
        case 1:
            face = 'A';
            worth = 11;
            break;
        case 2:
            face = '2';
            worth = 2;
            break;
        case 3:
            face = '3';
            worth = 3;
            break;
        case 4:
            face = '4';
            worth = 4;
            break;
        case 5:
            face = '5';
            worth = 5;
            break;
        case 6:
            face = '6';
            worth = 6;
            break;
        case 7:
            face = '7';
            worth = 7;
            break;
        case 8:
            face = '8';
            worth = 8;
            break;
        case 9:
            face = '9';
            worth = 9;
            break;
        case 10:
            face = 'T';
            worth = 10;
            break;
        case 11:
            face = 'J';
            worth = 10;
            break;
        case 12:
            face = 'Q';
            worth = 10;
            break;
        case 13:
            face = 'K';
            worth = 10;
            break;
        default:
            face = 'E';
            worth = 0;
            break;
    }

}


//Prototypes (Blackjack)
int blackjack (int &bank); //**1
void Cardp (vector<card> crd); //outputs all current cards in dealers hands
int Cardv (vector<card> crd); // returns values of cards.



int main() { 
    int bank(1000); //**1
    srand((unsigned)time(NULL));// seeding random.
    blackjack(bank);

    cout <<endl;
    system("PAUSE");
    return 0;
}
    
    
//Blackjack!!!!!!!!!!!!    
int blackjack (int &bank) { //**1

    vector<card> DC, PC; //total dealers cards, players cards.
    card crd; // new cards
    int bet(0); //**1
    char HS('h'); //Hit or Stay
    
    
    cout << "--------------------" <<endl;
    cout << "Welcome to Blackjack" <<endl;
    cout << "--------------------" <<endl;
    /* Insert menu here later. 
    cout << "Press 1: For rules" <<endl;
    cout << "Press 2: To play" <<endl;
    cout << "Press 3: To go back to main menu" <<endl;
    */
    
    while ( bank > 0 ) {
        bet = 0;
        DC.clear();
        PC.clear();
        HS = 'h';
        
        cout << "\nBank: " <<bank <<endl;
        cout << "Please enter a bet:"; //**1
        cin >> bet;
        bank -= bet;
        
        crd.random();
        DC.push_back(crd); //Push Back Dealers Card
        crd.random();
        DC.push_back(crd);
        crd.random();
        PC.push_back(crd); // Push Back Players Cards.
        crd.random();
        PC.push_back(crd);
        

        
        if (Cardv(PC) > 21) { // If Busts(22) then it checks for Ace. **99 
            for (int i = 0; i > PC.size(); i++) { 
                if (PC[i].face == 'A' && PC[i].worth == 11) {  // If Player card is Ace
                                PC[i].worth = 1; // Switch 11 to 1.
                                break;
                }
            }
        }
        
        if (Cardv(DC) > 21) { // If Busts(22)then it checks for Ace. **99
            for (int i = 0; i > PC.size(); i++) { 
                if (PC[i].face == 'A' && PC[i].worth == 11) {  // If Player card is Ace
                                PC[i].worth = 1; // Switch 11 to 1.
                                break;
                }
            }
        }
        
        
        
        cout << "Dealers Cards:"; //**2
        Cardp(DC); // Print DC **2.1
        cout <<endl; 
        cout << "Players Cards:";
        Cardp(PC); // Print PC
        cout <<endl;
        
        if (Cardv(PC) == 21) { // BLACKJACK
            cout << "Blackjack!!";
            bank += 3.5*bet;
            }
            
        else { //If blackjack isnt hit, go on with the game.
            while (Cardv(PC) < 21 && HS != 's') { //gets hit or stay information from player.
                cout << "Hit or Stay:";
                cin >> HS;
                if (HS == 'h') {
                    crd.random();
                    PC.push_back(crd);
                    Cardp(PC);
                    cout <<endl;
                }
                    if (Cardv(PC) > 21) { // If Busts then it checks for Ace. **99
                        for (int i = 0; i > PC.size(); i++) { 
                            if (PC[i].face =='A' && PC[i].worth == 11) {  // If Player card is Ace
                                PC[i].worth = 1; // Switch 11 to 1.
                                break;
                            }
                        }
                    }
            }
            
            if (Cardv(PC) > 21) {
                cout <<"Bust!!\n";
                cout << "--------------------" <<endl;
            }
            
            else {
                while (Cardv(DC) < 17) {
                    crd.random();
                    DC.push_back(crd);
                    if (Cardv(DC) > 21) { // If Busts then it checks for Ace. **99
                        for (int i = 0; i > PC.size(); i++) { 
                            if (DC[i].face =='A' && DC[i].worth == 11) {  // If Player card is Ace
                                            PC[i].worth = 1; // Switch 11 to 1.
                                            break;
                            }
                        }
                    }
                }
            
                cout << "Dealers Cards:"; //**2
                Cardp(DC); // Print DC **2.1
                cout <<endl;
                cout << "Players Cards:";
                Cardp(PC); // Print PC
                cout <<endl;
                
                if (Cardv(DC) < Cardv(PC) || Cardv(DC) > 21) { //You Win
                    cout << "You Win!!\n";
                    cout << "--------------------" <<endl;
                    bank += 2*bet;
                    }
                else {
                    cout << "You Lose!!\n";
                    cout << "--------------------" <<endl;
                }
            }
        }
    }
    
    if (bank <= 0) {
        bank = 0;
        cout << "Your Broke!";
    }
    

}

void Cardp (vector<card> crd) { //outputs all current cards in dealers hands
    for (int i = 0; i < crd.size(); i++) 
        cout << crd[i].face << crd[i].suit <<" ";
        
} 
int Cardv (vector<card> crd) { // returns values of cards.
    int val(0);
    
    for (int i = 0; i < crd.size(); i++)
        val += crd[i].worth;
    
    return val;
} 


[/PHP]I would appreciate any help you are willing to give.

---

