---
title: "GUI classes, graphical project, C++"
date: 2008-05-03
forum: Programming Talk
---

### Post by dodu3784 on 2008-05-03
Hi everybody,
I am programming in C++ a small project, trying to design end display a pendulum. I am using wxwidgets and OpenGL and I am facing kind of a "conceptual" problem. I want to display the evolution of my pendulum, however, I don't know how to make my GUI and Vue_OpenGL classes interact with this pendulum(called Pendule3D), could or how could I have one part of the code in Pendule3D.cc (for example the function dessine()) and call it in GUI.cc. How could I also create a Pendule3D in GUI.cc, because there's no main() section in it. Thank you very much for your answers

here is the code of GUI.h
```

#include "wx/wxprec.h"
#ifndef WX_PRECOMP
#include "wx/wx.h"
#endif

#ifndef GUI_H
#define GUI_H

#include "wx/glcanvas.h" // Pour combiner wxWidgets et OpenGL
#include"Pendule3D.h"
#include"Systeme.h"

// ----------------------------------------------------------------------
// Nouvelle application
class GUI : public wxApp
{	
public:
  bool OnInit();	
};

// ----------------------------------------------------------------------
// sous-fenetre de dessin OpenGL
class Vue_OpenGL : public wxGLCanvas
{
public:
  Vue_OpenGL( wxWindow*      parent
            , wxSize  const& taille   = wxDefaultSize     
            , wxPoint const& position = wxDefaultPosition
            );

  virtual ~Vue_OpenGL() { gluDeleteQuadric(sphere); }

  void InitOpenGL();

protected:
  void dessine(wxPaintEvent& evenement);
  void OnSize(wxSizeEvent& evenement);
  void OnKeyDown(wxKeyEvent& evenement);
  void OnEnterWindow(wxMouseEvent& evenement) { SetFocus(); }
  void OnTimer(wxTimerEvent& event);

  void RotateTheta(GLdouble deg);
  void RotatePhi(GLdouble deg);
  void deplace(double dr);
  
private:
  GLUquadric* sphere;
  double theta;
  double phi;
  double r;
	Pendule3D p;
	

  // le "Timer"
  wxTimer* timer;
  static int TIMER_ID;

  // le paramètre dépendant du temps
  double position;

DECLARE_EVENT_TABLE()
};

// ----------------------------------------------------------------------
// fenetre(s) principale(s)
class Fenetre: public wxFrame
{
public:
  Fenetre( wxString const& titre 
         , wxSize   const& taille   = wxDefaultSize
         , wxPoint  const& position = wxDefaultPosition
         , long            style    = wxDEFAULT_FRAME_STYLE
         );

  virtual ~Fenetre() {}

protected:
  void OnExit(wxCommandEvent& event) { Close(true); }

  Vue_OpenGL* fogl;

DECLARE_EVENT_TABLE()
};

#endif

``` 

for GUI.cc

```

#include "wx/wxprec.h"
#ifndef WX_PRECOMP
#include "wx/wx.h"
#endif

#include "wx/glcanvas.h" // Pour combiner wxWidgets et OpenGL
#include"GUI.h"

/* ===================================================================
   Implementation de Vue_OpenGL
   =================================================================== */

int Vue_OpenGL::TIMER_ID(12);

BEGIN_EVENT_TABLE(Vue_OpenGL, wxGLCanvas)
    EVT_PAINT(          Vue_OpenGL::dessine       )
    EVT_SIZE(           Vue_OpenGL::OnSize        )
    EVT_KEY_DOWN(       Vue_OpenGL::OnKeyDown     )
    EVT_ENTER_WINDOW(   Vue_OpenGL::OnEnterWindow )
    EVT_TIMER(TIMER_ID, Vue_OpenGL::OnTimer       )
END_EVENT_TABLE()

// ======================================================================
Vue_OpenGL::Vue_OpenGL( wxWindow*      parent
                      , wxSize  const& taille
                      , wxPoint const& position
                      )
: wxGLCanvas(parent, wxID_ANY, position, taille, 
             wxSUNKEN_BORDER|wxFULL_REPAINT_ON_RESIZE , wxT("") )
, sphere(gluNewQuadric())
, theta(35.0), phi(20.0), r(5.0)
, timer(new wxTimer(this, TIMER_ID))
, position(0.0)
	
	
{
	Vecteur a1(1,0,0);
	Vecteur o1(0,0,0);

	double init1[1]={0.78};
	double init2[1]={0};

	Vecteur param1(init1, 1);
	Vecteur vite1(init2, 1);

	Pendule3D p1(4.32, 0.81, 0.33, param1, vite1, a1, o1,  o1);

	this->p=p1;

}

// ======================================================================

void Vue_OpenGL::dessine(wxPaintEvent&)
{

  if (!GetContext()) return;

  SetCurrent();

  // commence par effacer l'ancienne image
  glClear(GL_COLOR_BUFFER_BIT | GL_DEPTH_BUFFER_BIT);

  /* part du système de coordonnées de base 
   * (dessin à l'origine : matrice identité) */
  glMatrixMode(GL_MODELVIEW);
  glLoadIdentity();

  // place la caméra
  gluLookAt(r,   0.0, 0.0,
            0.0, 0.0, 0.0,
            0.0, 0.0, 1.0);
  glRotated(theta, 0.0, 1.0, 0.0); 
  glRotated(phi,   0.0, 0.0, 1.0);

  // dessin de la première sphère
  glPushMatrix();                // Sauvegarder l'endroit où l'on se trouve
  glTranslated(-1.0, 0.0, 0.5);  /* Se positionner à l'endroit où l'on veut
				  * dessiner                                */
  glColor4d(0.0, 0.0, 1.0, 1.0); // Choisir la couleur (bleu ici)
  gluSphere(sphere, 1.0, 30, 30);// Dessiner une sphère
  glPopMatrix();                 // Revenir à l'ancienne position

  // dessin de la seconde sphère
  glPushMatrix();
  glTranslated(0.0, 0.0, 0.0); 
  glColor4d(0.0, 1.0, 1.0, 1.0); // choisi la couleur (turquoise ici)
  gluSphere(sphere, 1.5, 50, 50);
  glPopMatrix();

  // dessin de la troisième sphère
  glPushMatrix();
  glTranslated(1.0, 0.0, 0.5);
  glColor4d(0.0, 0.8, 0.0, 1.0);  //vert
  gluSphere(sphere, 1.0, 50, 50);
  glPopMatrix();

  // Dessin de la petite sphère qui tourne
  glPushMatrix();
  glRotated(position, 0.0, 0.0, 1.0); /* on la fait tourner de "position" 
                                       * autour de Oz...                   */
  glTranslated(2.0, 0.0, 0.0);        /* ...sur un cercle de rayon 2.0     */
  glColor4d(1.0, 0.0, 0.0, 1.0); // couleur rouge
  gluSphere(sphere, 0.1, 30, 30);
  glPopMatrix();

  // Finalement, on envoie le dessin à l'écran
  glFlush();
  SwapBuffers();
}


// ======================================================================
void Vue_OpenGL::OnSize(wxSizeEvent& event)
{
  // Nécessaire pour mettre à jour le contexte sur certaines plateformes
  wxGLCanvas::OnSize(event);

  if (GetContext()) {
    // set GL viewport (not called by wxGLCanvas::OnSize on all platforms...)
    int w, h;
    GetClientSize(&w, &h);
    SetCurrent();
    glViewport(0, 0, (GLint) w, (GLint) h);
  } 
}

// ======================================================================
void Vue_OpenGL::OnKeyDown( wxKeyEvent& event )
{
  switch( event.GetKeyCode() ) {
  case WXK_LEFT: 
    RotatePhi( 2.0);
    Refresh(false);
    break;

  case WXK_RIGHT: 
    RotatePhi( -2.0);
    Refresh(false);
    break;

  case WXK_UP: 
    RotateTheta( 2.0);
    Refresh(false);
    break;

  case WXK_DOWN: 
    RotateTheta(-2.0);
    Refresh(false);
    break;

  case WXK_HOME:
    r     =  5.0;   // On revient à un point fixé
    theta = 35.0;
    phi   = 20.0;
    Refresh(false);
    break;

  case WXK_PAGEUP:
    deplace(-1.0);    // On se rapproche
    Refresh(false);
    break;

  case WXK_PAGEDOWN:
    deplace(1.0);     // On s'éloigne
    Refresh(false);
    break;

  // Pause sur la touche "espace"
  case ' ':
    if (timer->IsRunning()) {
      timer->Stop();
    } else {
      timer->Start();
    }
    break;
  }
  
  event.Skip();
}

// ======================================================================
void Vue_OpenGL::RotateTheta(GLdouble deg)
{
  theta += deg;
  while (theta < -180.0) { theta += 360.0; }
  while (theta >  180.0) { theta -= 360.0; }
}

// ======================================================================
void Vue_OpenGL::RotatePhi(GLdouble deg)
{
  phi += deg;
  while (phi <   0.0) { phi += 360.0; }
  while (phi > 360.0) { phi -= 360.0; }
}

// ======================================================================
void Vue_OpenGL::deplace(GLdouble dr)
{
  r += dr;
  if (r < 1.0) r = 1.0;
  else if (r > 1000.0) r = 1000.0;
}

// ======================================================================
void Vue_OpenGL::InitOpenGL() 
{
  // Initialisation OpenGL

  SetCurrent();

  // active la gestion de la profondeur
  glEnable(GL_DEPTH_TEST);    

  // fixe la perspective
  glMatrixMode(GL_PROJECTION);
  glLoadIdentity();
  gluPerspective(65.0, 4./3., 1.0, 1000.0);

  // fixe la couleur du fond à noir
  glClearColor(0.0, 0.0, 0.0, 1.0);

  // lance le Timer
  timer->Start(20);
}

// ======================================================================
void Vue_OpenGL::OnTimer(wxTimerEvent& event)
{
  // mise à jour de la position à partir du pas de temps (via une
  // vitesse, arbitraire ici)
  position += event.GetInterval() / 15.0;
  while (position > 360.0) position -= 360.0;

  // demande l'affichage
  Refresh(false);
}

/* ===================================================================
   Implementation de Fenetre
   =================================================================== */

BEGIN_EVENT_TABLE(Fenetre, wxFrame)
    EVT_MENU( wxID_EXIT, Fenetre::OnExit )
END_EVENT_TABLE()

// ======================================================================
Fenetre::Fenetre( wxString const& titre 
                , wxSize   const& taille
                , wxPoint  const& position
                , long            style
                )
: wxFrame(0, wxID_ANY, titre, position, taille, style)
, fogl(new Vue_OpenGL(this))
{
  // Barre de menu
  wxMenu* winMenu = new wxMenu;
  winMenu->Append(wxID_EXIT, wxT("&Close"));

  wxMenuBar* menuBar = new wxMenuBar;
  menuBar->Append(winMenu, wxT("&Window"));

  SetMenuBar(menuBar);

  // Affiche (montre) la fenetre
  Show(true);

  // Initialise OpenGL
  fogl->InitOpenGL();
}

/* ===================================================================
   Implementation de l'application principale
   =================================================================== */

// ======================================================================
bool GUI::OnInit()
{
  // Crée la fenêtre principale
  Fenetre* f = new Fenetre(wxT("Simulation temps reel"),
                           wxSize(800, 600));
  SetTopWindow(f);
  return (f != 0);
}

/* ===================================================================
   Equivalent de main()
   =================================================================== */



```

Pendule3D.h
```

#include "wx/wxprec.h"
#ifndef WX_PRECOMP
#include "wx/wx.h"
#endif

#ifndef PENDULE3D_H
#define PENDULE3D_H

#include "wx/glcanvas.h"
#include<iostream>
#include"oscillateur.h"
#include"vecteur.h"
using namespace std;

//P6

class Pendule3D : public Oscillateur
{
private:
	double masse;
	double longueur;
	double ftm_fluides;
	Vecteur axe;
	Vecteur origine;
	Vecteur position;
public:
	Vecteur equation_evolution();
	
	Pendule3D(double m, double l, double f, Vecteur  parametres1, Vecteur vitesse1, Vecteur  axe1, Vecteur origine1, Vecteur position1);
	Oscillateur* copie() const{return new Pendule3D(*this);}
	
	double get_masse () const {return masse;}
	double get_longueur () const {return longueur;}
	double get_ftm_fluides () const {return ftm_fluides;}
	
	Vecteur get_axe() const {return axe;}
	Vecteur get_origine() const {return origine;}
	Vecteur get_position() const {return position;}

	void dessine(double r, double theta, double phi, wxSize const& position);
};

#endif


```

and finally Pendule3D.cc

```

#include<iostream>
#include<cmath>
#include<vector>
//#include"vecteur.h"
//#include"oscillateur.h"
#include"Pendule.h"
using namespace std;

Pendule::Pendule(double m, double l, double f, Vecteur  parametres1, Vecteur vitesse1, Vecteur axe1, Vecteur origine1)
	: Oscillateur(parametres1, vitesse1), masse(m), longueur(l), ftm_fluides(f), axe(axe1), origine(origine1)
{}


Vecteur Pendule::equation_evolution()
{
	double alpha(0);
	
	alpha=(-9.81/longueur) * sin(parametres.get_corpus()[0]) -
		(ftm_fluides/(masse*longueur*longueur))* vitesse.get_corpus()[0]-
		Vecteur(0, 0, -9.81) * axe ;
	
	double tab[1]={alpha};


	return Vecteur(tab, 1);
}

//g defini arbitrairement, on sait de plus que parametres a comme premier coefficient, l'angle theta

```

---

### Post by soaresnew on 2008-05-03
What'd you mean exactly by the 'evolution' of your pendulum? 

The swing time of it, or something else, and are you creating this from an ide?  Which one are you using exactly?

"because there's no main() section in it"

Then create a main section in it; I need some idea of what you're trying to do with your pendulum, most of your GUI code is void-- it will return nothing if you want an event to transpire.

---

