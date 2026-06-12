---
title: "Python--Adding Error checking to &quot;card&quot; game"
date: 2009-11-30
forum: Programming Talk
---

### Post by Z47isthenew42 on 2009-11-30
I have been teaching myself Python using * Python Programming for the Absolute Beginner, Second Edition* by Michael Dawson.  He includes challenges at the end of each chapter.  One of the challenges is to add needed error checking to a blackjack program, such as making sure there are enough "cards" in the "deck" before a new round begins.  The starting code of the blackjack program before any error-checking is added is as follows:

[php] # Blackjack

# From 1 to 7 players compete against a dealer



import cards, games     



class BJ_Card(cards.Card):

    """ A Blackjack Card. """

    ACE_VALUE = 1

    

    def get_value(self):

        if self.is_face_up:

            value = BJ_Card.RANKS.index(self.rank) + 1

            if value > 10:

                value = 10

        else:

            value = None

        return value



    value = property(get_value)





class BJ_Deck(cards.Deck):

    """ A Blackjack Deck. """

    def populate(self):

        for suit in BJ_Card.SUITS: 

            for rank in BJ_Card.RANKS: 

                self.cards.append(BJ_Card(rank, suit))

    



class BJ_Hand(cards.Hand):

    """ A Blackjack Hand. """

    def __init__(self, name):

        super(BJ_Hand, self).__init__()

        self.name = name



    def __str__(self):

        rep = self.name + ":\t" + super(BJ_Hand, self).__str__()  

        if self.total:

            rep += "(" + str(self.total) + ")"        

        return rep

     

    def get_total(self):

        # if a card in the hand has value of None, then total is None

        for card in self.cards:

            if not card.value:

                return None

        

        # add up card values, treat each Ace as 1

        total = 0

        for card in self.cards:

              total += card.value



        # determine if hand contains an Ace

        contains_ace = False

        for card in self.cards:

            if card.value == BJ_Card.ACE_VALUE:

                contains_ace = True

                

        # if hand contains Ace and total is low enough, treat Ace as 11

        if contains_ace and total <= 11:

            # add only 10 since we've already added 1 for the Ace

            total += 10   

                

        return total



    total = property(get_total)



    def is_busted(self):

        return self.total > 21





class BJ_Player(BJ_Hand):

    """ A Blackjack Player. """

    def is_hitting(self):

        response = games.ask_yes_no("\n" + self.name + ", do you want a hit? (Y/N): ")

        return response == "y"



    def bust(self):

        print self.name, "busts."

        self.lose()



    def lose(self):

        print self.name, "loses."



    def win(self):

        print self.name, "wins."



    def push(self):

        print self.name, "pushes."



        

class BJ_Dealer(BJ_Hand):

    """ A Blackjack Dealer. """

    def is_hitting(self):

        return self.total < 17



    def bust(self):

        print self.name, "busts."



    def flip_first_card(self):

        first_card = self.cards[0]

        first_card.flip()





class BJ_Game(object):

    """ A Blackjack Game. """

    def __init__(self, names):      

        self.players = []

        for name in names:

            player = BJ_Player(name)

            self.players.append(player)



        self.dealer = BJ_Dealer("Dealer")



        self.deck = BJ_Deck()

        self.deck.populate()

        self.deck.shuffle()



    def get_still_playing(self):

        remaining = []

        for player in self.players:

            if not player.is_busted():

                remaining.append(player)

        return remaining



    # list of players still playing (not busted) this round

    still_playing = property(get_still_playing)



    def __additional_cards(self, player):

        while not player.is_busted() and player.is_hitting():

            self.deck.deal([player])

            print player

            if player.is_busted():

                player.bust()

           

    def play(self):

        # deal initial 2 cards to everyone

        self.deck.deal(self.players + [self.dealer], per_hand = 2)

        self.dealer.flip_first_card()    # hide dealer's first card

        for player in self.players:

            print player

        print self.dealer



        # deal additional cards to players

        for player in self.players:

            self.__additional_cards(player)



        self.dealer.flip_first_card()    # reveal dealer's first 



        if not self.still_playing:

            # since all players have busted, just show the dealer's hand

            print self.dealer

        else:

            # deal additional cards to dealer

            print self.dealer

            self.__additional_cards(self.dealer)



            if self.dealer.is_busted():

                # everyone still playing wins

                for player in self.still_playing:

                    player.win()                    

            else:

                # compare each player still playing to dealer

                for player in self.still_playing:

                    if player.total > self.dealer.total:

                        player.win()

                    elif player.total < self.dealer.total:

                        player.lose()

                    else:

                        player.push()



        # remove everyone's cards

        for player in self.players:

            player.clear()

        self.dealer.clear()

        



def main():

    print "\t\tWelcome to Blackjack!\n"

    

    names = []

    number = games.ask_number("How many players? (1 - 7): ", low = 1, high = 8)

    for i in range(number):

        name = raw_input("Enter player name: ")

        names.append(name)

    print

        

    game = BJ_Game(names)



    again = None

    while again != "n":

        game.play()

        again = games.ask_yes_no("\nDo you want to play again?: ")





main()

raw_input("\n\nPress the enter key to exit.")

[/php]

The code for the cards module is as follows:

[php]
# Cards Module
# Basic classes for a game with playing cards

# create Card class
class Card(object):
	""" A playing card. """
	RANKS = ["A", "2", "3", "4", "5", "6", "7",
			"8", "9", "10", "J", "Q", "K"]
	SUITS = ["c", "d", "h", "s"]
	def __init__(self, rank, suit, face_up = True):
		self.rank = rank
		self.suit = suit
		self.is_face_up = face_up
	
	def __str__(self):
		if self.is_face_up:
			rep = self.rank + self.suit
		else:
			rep = "XX"
		return rep
	
	def flip(self):
		self.is_face_up = not self.is_face_up

class Hand(object):
	""" A hand of playing cards. """
	def __init__(self):
		self.cards = []
	
	def __str__(self):
		if self.cards:
			rep = ""
			for card in self.cards:
				rep += str(card) + "\t"
		else:
			rep = "<empty>"
		return rep
	
	def clear(self):
		self.cards = []
	
	def add(self, card):
		self.cards.append(card)
	
	def give(self, card, other_hand):
		self.cards.remove(card)
		other_hand.add(card)

class Deck(Hand):
	""" A deck of playing cards. """
	def populate(self):
		for suit in Card.SUITS:
			for rank in Card.RANKS:
				self.add(Card(rank, suit))
	def shuffle(self):
		import random
		random.shuffle(self.cards)
	
	def deal(self, hands, per_hand = 1):
		for rounds in range(per_hand):
			for hand in hands:
				if self.cards:
					top_card = self.cards[0]
					self.give(top_card, hand)
				else:
					print "Can't continue deal. Out of cards!"

if __name__ == "__main__":
	print "This is a module with classes for playing cards."
	raw_input("\n\nPress the enter key to exit.")
[/php]

And the code for the games module is:

[php]
# Games
# Demonstrates module creation

class Player(object):
	""" A player for a game. """
	def __init__(self, name, score = 0):
		self.name = name
		self.score = score
	
	def __str__(self):
		rep = self.name + ":\t" + str(self.score)
		return rep

def ask_yes_no(question):
	"""Ask a yes or no question."""
	response = None
	while response not in ("y", "n"):
		response = raw_input(question).lower()
	return response

def ask_number(question, low, high):
	"""Ask for a number within a range."""
	response = None
	while response not in range(low, high):
		response = int(raw_input(question))
	return response

if __name__ == "__main__":
	print "You ran this module directly (and did not import it)."
	raw_input("\n\nPress the enter key to exit.")
[/php]

I am specifically having trouble adding a way to ensure there are enough cards in the deck, so any help will be appreciated.  I will continue trying to add this and other error-checking and report my results.

---

### Post by nelfin on 2009-11-30
I'm not exactly sure what mean by error checking, but it should be possible to extend the BJ_Deck class to make it automatically "re-shuffle" when the number of undealt cards falls below a certain level (say, two times the number of players plus the dealer, enough cards to start another round).

Class inheritance works by having a child class inherit all of it's parents members and methods (variables and functions) if they are not overridden in the child. For example, the BJ_Deck overrides cards.Deck's populate(), but not its deal().

By defining a deal() function in BJ_Deck you should be able to get the functionality you want:

e.g.
[PHP]class BJ_Deck(cards.Deck):
    """ A Blackjack Deck. """
    ...
    def deal(self, hands, per_hand = 1):
        for rounds in range(per_hand):
            for hand in hands:
                if len(self.cards) >= (per_hand * len(hands)):
                    top_card = self.cards[0]
                    self.give(top_card, hand)
                else:
                    print "Reshuffling deck."
                    self.cards = []
                    self.populate()
                    self.shuffle()
                    # Remember to deal out a card:
                    top_card = self.cards[0]
                    self.give(top_card, hand)[/PHP]

Alternatively, you could just have
[PHP]if self.cards:
    ...
else:
    print "Deck empty. Reshuffling."
    self.populate()
    self.shuffle()
    ...[/PHP]

---

### Post by Z47isthenew42 on 2009-12-03
Thank you.  That was much more elegant (and probably the more proper way) to solve the problem than the way I found out how to do.

As the "error-checking" terminology:  That was simply the term the author of the book used, so I used it as well.

---

