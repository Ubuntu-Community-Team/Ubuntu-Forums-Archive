---
title: "experiencing random errors with curses and python"
date: 2012-01-29
forum: Programming Talk
---

### Post by creatureofthedark on 2012-01-29
Hi,

Iv been working on this application for a while now and for some reason I keep getting odd formatting on my screen when running it... 
these are entirely random... 
sometimes I can start the application move up and down with no issues and then when I run it again it all goes crazy.... 
I have attached screen shots to show the results...

the application is supposed to pull alerts from a mysql database and display them in the console. the user should then be able to move up and down using arrow keys to select the alert and bring up more info on it [not got this far yet...]

the other issue is the info sub-window brakes everything.. so I have had do comment it out for now...

any help in fixing this would be GREAT!!! currently the only thing I can guess is the screen thread is reading from the select_poss at the same time as the main thread is writing to it.. iv tried using locks but that made things worse.. [could be I did that wrong to...]


```
import curses, traceback, threading#, time
import MySQLdb, sys
#Globals
poss_y = 0
select_poss = 0

def main(stdscr):
#Show Head Tital
	head = stdscr.subwin(3,79,0,0)
	head.box()
	head.addstr(1, 20, " WELCOM TO ANOC v0.2 ", curses.A_BOLD)
	head.addstr(1, 40, "  --  Monitoring Console ")

	#info = stdscr.subwin(20,50,30,0)
	#info.box()

#Set Global variables for monitoring console possitioning
	global poss_y
	global select_poss
	


#Start Refresh Trhead
	#thread.start_new_thread(console_update, (poss_y, select_poss))
	ref = threading.Thread(target=console_update)
	ref.setDaemon(True)
	ref.start()
	
#Start Controle Loop
	event = "t"
	while True:
		event = stdscr.getch()
		if event == ord("q"):
			#ref.stop() 
			break
		elif str(event) == "258": select_poss += 1 

		elif str(event) == "259": select_poss -= 1 

		head.refresh()



def console_update():
	global select_poss
	while True:
		con_x = 3
		con_y = 1

		console = curses.newpad(40, 79) #Set console as a pad that is 40 chars long and 79 wide
		console.box()

		#console.noutrefresh()
		#console.erase()

		cur.execute("SELECT * FROM Alerts")
		size = int(cur.rowcount)

		if select_poss >= size : select_poss = 0
		if select_poss < 0 : select_poss = size

		for i in range(size):
			if i == select_poss:
				data = cur.fetchone()
				console.addstr(con_y, con_x, data[1], curses.color_pair(1))
				con_y += 1
				console.addstr(con_y, con_x, data[2], curses.color_pair(1))
				con_y += 1
				console.hline(con_y, 1, curses.ACS_HLINE, 77)
				con_y += 1
			else:
				data = cur.fetchone()
				console.addstr(con_y, con_x, data[1], curses.A_BOLD)
				con_y += 1
				console.addstr(con_y, con_x, data[2])
				con_y += 1
				console.hline(con_y, 1, curses.ACS_HLINE, 77)
				con_y += 1
			
		console.addstr(con_y, con_x, "select_poss is currently", curses.color_pair(2))
		con_y += 1
		console.addstr(con_y, con_x, str(select_poss),curses.color_pair(2))
		con_y += 1
		console.hline(con_y, 1, curses.ACS_HLINE, 77)
		con_y += 1

		#console.doupdate(poss_y,0, 3,0, 20,79)
		console.refresh(poss_y,0, 3,0, 20,79)


if __name__ == '__main__':
	try:
##########################
##	Setup Curses	##
##########################		
		stdscr=curses.initscr()
		curses.noecho()
		curses.cbreak()
		curses.curs_set(0)
		stdscr.keypad(1)
		curses.start_color()
		curses.init_pair(1, curses.COLOR_WHITE, curses.COLOR_BLUE)
		curses.init_pair(2, curses.COLOR_BLACK, curses.COLOR_GREEN)

##########################
##	Connect to DB	##
##########################
		global cur
		conn = None
		conn = MySQLdb.Connection(db='testdb', user='anocsys', passwd='anocpass')
		cur = conn.cursor()

##########################
##	Start main	##
##########################
		main(stdscr)

##########################
##	Close Curses	##
##########################
		stdscr.keypad(0)
		curses.echo()
		curses.nocbreak()
		curses.endwin()

	except:
##########################
##	Close Curses	##
##	When Error	##
##########################		
		stdscr.keypad(0)
		curses.echo()
		curses.nocbreak()
		curses.endwin()
		traceback.print_exc()   #prints the exception that broke everything
```

---

### Post by creatureofthedark on 2012-01-31
seem to have fixed it :P

swapped the refresh of the console to the main thread on the arrow keys to the thread.. dunno why it works but it dose.... probably something to do with it being a daemon thread... who knows...

---

