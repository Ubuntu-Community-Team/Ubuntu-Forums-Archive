---
title: "g++ &quot;undefined reference to ...&quot; error..please help"
date: 2012-01-16
forum: Programming Talk
---

### Post by ldkz2524 on 2012-01-16
my program compiles perfectly on Visual Studio, but fails to compile in g++ due to 
main.cpp:(.text+0x4c): undefined reference to `Game::Game(int, int, int)'
main.cpp:(.text+0x58): undefined reference to `Game::play()'
main.cpp:(.text+0x64): undefined reference to `Game::~Game()'
main.cpp:(.text+0x95): undefined reference to `Game::~Game()'
```
#include "Game.h"
#include <ctime>
using namespace std;
int main()
{
    srand(static_cast<unsigned int>(time(0)));
    Game g(10, 12, 50);
    g.play();
}

```
```

#ifndef GAME_INCLUDED
#define GAME_INCLUDED
#include <string>
class Arena;
class Game
{
  public:
    Game(int rows, int cols, int nRobots);
    ~Game();
    void play();
  private:
    Arena* m_arena;
    std::string takePlayerTurn();
    std::string takeRobotsTurn();
};
bool recommendMove(const Arena& a, int r, int c, int& bestDir);
int computeDanger(const Arena& a, int r, int c);
#endif

```
```

#include <iostream>
#include <string>
#include <cassert>
#include "Game.h"
#include "globals.h"
#include "Arena.h"
#include "Player.h"
#include "History.h"
///////////////////////////////////////////////////////////////////////////
//  Game implementation
///////////////////////////////////////////////////////////////////////////

Game::Game(int rows, int cols, int nRobots)
{
    if (nRobots < 0  ||  nRobots > MAXROBOTS)
    {
        std::cout << "***** Game created with invalid number of robots:  "
             << nRobots << std::endl;
        std::exit(1);
    }

    int nEmpty = rows * cols - nRobots - 1;  // 1 for Player
    if (nEmpty < 0)
    {
        std::cout << "***** Game created with a " << rows << " by "
             << cols << " arena, which is too small too hold a player and "
             << nRobots << " robots!" << std::endl;
        std::exit(1);
    }

      // Create arena
    m_arena = new Arena(rows, cols);

      // Add some walls in WALL_DENSITY of the empty spots
    assert(WALL_DENSITY >= 0  &&  WALL_DENSITY <= 1);
    int nWalls = static_cast<int>(WALL_DENSITY * nEmpty);
    while (nWalls > 0)
    {
        int r = randInt(1, rows);
        int c = randInt(1, cols);
        if (m_arena->getCellStatus(r, c) == WALL)
            continue;
        m_arena->setCellStatus(r, c, WALL);
        nWalls--;
    }

      // Add player
    int rPlayer;
    int cPlayer;
    do
    {
        rPlayer = randInt(1, rows);
        cPlayer = randInt(1, cols);
    } while (m_arena->getCellStatus(rPlayer, cPlayer) != EMPTY);
    m_arena->addPlayer(rPlayer, cPlayer);

      // Populate with robots
    while (nRobots > 0)
    {
        int r = randInt(1, rows);
        int c = randInt(1, cols);
        if (m_arena->getCellStatus(r,c) != EMPTY  ||  (r == rPlayer && c == cPlayer))
            continue;
        m_arena->addRobot(r, c, randInt(1, MAXCHANNELS));
        nRobots--;
    }
}

Game::~Game()
{
    delete m_arena;
}

std::string Game::takePlayerTurn()
{
    for (;;)
    {
        std::cout << "Your move (n/e/s/w/x/h or nothing): ";
        std::string playerMove;
        getline(std::cin, playerMove);

        if (playerMove == "h")
        {
			m_arena ->history().display();
            std::cout << "Press enter to continue.";
            std::cin.ignore(100000, '\n');
            m_arena->display("");
            continue;
        }

        Player* player = m_arena->player();
        int dir;

        if (playerMove.size() == 0)
        {
            if (recommendMove(*m_arena, player->row(), player->col(), dir))
                return player->move(dir);
            else
                return player->stand();
        }
        else if (playerMove.size() == 1)
        {
            if (tolower(playerMove[0]) == 'x')
                return player->stand();
            else if (charToDir(playerMove[0], dir))
                return player->move(dir);
        }
        std::cout << "Player move must be nothing, or 1 character n/e/s/w/x/h." << std::endl;
    }
}

std::string Game::takeRobotsTurn()
{
    for (;;)
    {
        std::cout << "Broadcast (e.g., 2n): ";
        std::string broadcast;
        getline(std::cin, broadcast);
        if (broadcast.size() != 2)
            std::cout << "Broadcast must be channel followed by direction." << std::endl;
        else if (broadcast[0] < '1'  ||  broadcast[0] > '0'+MAXCHANNELS)
            std::cout << "Channel must be a valid digit." << std::endl;
        else
        {
            int dir;
            if (charToDir(broadcast[1], dir))
                return m_arena->moveRobots(broadcast[0]-'0', dir);
            else
                std::cout << "Direction must be n, e, s, or w." << std::endl;
        }
    }
}

void Game::play()
{
    m_arena->display("");
    while ( ! m_arena->player()->isDead()  &&  m_arena->robotCount() > 0)
    {
        std::string msg = takePlayerTurn();
        m_arena->display(msg);
        Player* player = m_arena->player();
        if (player->isDead())
            break;
        msg = takeRobotsTurn();
        m_arena->display(msg);
    }
    if (m_arena->player()->isDead())
        std::cout << "You lose." << std::endl;
    else
        std::cout << "You win." << std::endl;
}
  // Recommend a move for a player at (r,c):  A false return means the
  // recommendation is that the player should stand; otherwise, bestDir is
  // set to the recommended direction to move.
bool recommendMove(const Arena& a, int r, int c, int& bestDir)
{
      // How dangerous is it to stand?
    int standDanger = computeDanger(a, r, c);

      // if it's not safe, see if moving is safer
    if (standDanger > 0)
    {
        int bestMoveDanger = standDanger;
        int bestMoveDir = NORTH;  // arbitrary initialization

          // check the four directions to see if any move is
          // better than standing, and if so, record the best
        for (int dir = 0; dir < NUMDIRS; dir++)
        {
            int rnew = r;
            int cnew = c;
            if (attemptMove(a, dir, rnew, cnew))
            {
                int danger = computeDanger(a, rnew, cnew);
                if (danger < bestMoveDanger)
                {
                    bestMoveDanger = danger;
                    bestMoveDir = dir;
                }
            }
        }

          // if moving is better than standing, recommend move
        if (bestMoveDanger < standDanger)
        {
            bestDir = bestMoveDir;
            return true;
        }
    }
    return false;  // recommend standing
}
int computeDanger(const Arena& a, int r, int c)
{
      // Our measure of danger will be the number of robots that might move
      // to position r,c.  If a robot is at that position, it is fatal,
      // so a large value is returned.

    if (a.numberOfRobotsAt(r,c) > 0)
        return MAXROBOTS+1;

    int danger = 0;
    if (r > 1)
        danger += a.numberOfRobotsAt(r-1,c);
    if (r < a.rows())
        danger += a.numberOfRobotsAt(r+1,c);
    if (c > 1)
        danger += a.numberOfRobotsAt(r,c-1);
    if (c < a.cols())
        danger += a.numberOfRobotsAt(r,c+1);

    return danger;
}
```
There is more files included in this program, but i guess the problem is coming from these three files

---

### Post by gateway67 on 2012-01-16
You need to create object files of each of your modules before you attempt to link them to form an executable.  Or you could compile all of your modules at once to form the executable.

Choose one of these methods:
```

g++ -c Main.cpp
g++ -c Game.cpp
...
g++ Main.o Game.o -o game

```
Or
```

g++ Main.cpp Game.cpp Etc.cpp -o game

```

---

### Post by ldkz2524 on 2012-01-16
Thanks, i guess i was missing out the most important part.
I found a different solution thou.
i compiled the program using g++ with following code:
g++ -o main *.cpp
main is just a random name i gave it and *.cpp just compiles every cpp files in the folder

---

