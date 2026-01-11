# TP : Publier son site web avec GitHub Pages

**BUT Réseau et Télécoms - 1ère année**  
**Durée estimée : 2 heures**

---

## 🎯 Objectifs du TP

À la fin de ce TP, vous serez capable de :
- Comprendre les concepts fondamentaux du **contrôle de version** avec Git
- Créer et configurer un compte GitHub
- Utiliser Git en ligne de commande pour gérer votre code
- Publier votre site web HTML/CSS sur **GitHub Pages**
- Collaborer efficacement avec d'autres développeurs

---

## 📚 Introduction : Qu'est-ce que le contrôle de version ?

### Pourquoi le contrôle de version est essentiel

Imaginez que vous travaillez sur un projet de développement web. Vous apportez des modifications, ajoutez de nouvelles fonctionnalités, puis réalisez que votre dernière modification a tout cassé. Sans contrôle de version, vous devriez tout refaire manuellement ou espérer avoir fait une sauvegarde récente.

Le **contrôle de version** (ou *source control*) est un système qui enregistre les modifications apportées à vos fichiers au fil du temps. C'est comme une **machine à remonter le temps** pour votre code.

### Les avantages du contrôle de version

1. **Historique complet** : Chaque modification est enregistrée avec qui l'a faite, quand et pourquoi
2. **Retour en arrière** : Vous pouvez revenir à n'importe quelle version précédente
3. **Collaboration** : Plusieurs personnes peuvent travailler simultanément sur le même projet
4. **Branches** : Vous pouvez expérimenter sans risquer de casser le code principal
5. **Sauvegarde** : Votre code est stocké sur des serveurs distants (comme GitHub)

### Git et GitHub : quelle différence ?

- **Git** : C'est le logiciel de contrôle de version que vous installez sur votre ordinateur
- **GitHub** : C'est une plateforme en ligne qui héberge vos projets Git et facilite la collaboration

Analogie : Git est comme Word (le logiciel), GitHub est comme OneDrive (le stockage en ligne).

---

## ⚠️ IMPORTANT : Configuration du navigateur

**Avant de commencer, lisez attentivement cette section !**

### Désactivez la traduction automatique

Si vous utilisez un navigateur avec la traduction automatique activée (Chrome, Edge, etc.), **désactivez-la immédiatement** pour les sites de développement comme GitHub, Stack Overflow, documentation technique, etc.

### Pourquoi c'est critique ?

Le développement informatique se fait **en anglais**. Les mots-clés, fonctions et commandes sont en anglais. Si votre navigateur traduit automatiquement :

```python
# Code original (qui fonctionne)
print("Hello")
read("file.txt")

# Code traduit par le navigateur (qui NE fonctionne PAS)
imprime("Bonjour")
lit("fichier.txt")
```

❌ **Résultat** : Votre code ne fonctionnera jamais !

### Comment désactiver la traduction

**Sur Chrome/Edge :**
1. Paramètres → Langues
2. Décochez "Me proposer de traduire les pages..."
3. Ou cliquez sur l'icône de traduction dans la barre d'adresse et sélectionnez "Ne jamais traduire ce site"

**Conseil pro** : Apprenez le vocabulaire technique en anglais dès maintenant. C'est un investissement qui vous servira toute votre carrière !

---

## 📝 Étape 0 : Prérequis

Avant de commencer, assurez-vous d'avoir :
- ✅ Un site web HTML/CSS fonctionnel (celui créé lors du TP précédent)
- ✅ Visual Studio Code installé
- ✅ Une adresse email valide

---

## 🆕 Étape 1 : Créer un compte GitHub

### 1.1 Inscription

1. Rendez-vous sur [github.com](https://github.com)
2. Cliquez sur **Sign up** (S'inscrire)
3. Remplissez le formulaire :
   - **Email** : Utilisez votre email universitaire ou personnel
   - **Password** : Choisissez un mot de passe fort (minimum 15 caractères ou 8 avec des chiffres et minuscules)
   - **Username** : Choisissez un nom d'utilisateur professionnel (il sera visible publiquement)
     - ✅ Bon : `jean-dupont`, `jdupont-dev`, `jeandupont`
     - ❌ Évitez : `xX_dark_coder_Xx`, `kikoolol123`

### 1.2 Vérification

1. Vérifiez votre email et cliquez sur le lien de confirmation
2. Connectez-vous à GitHub
3. Vous pouvez sauter les questions optionnelles sur vos centres d'intérêt

**🎉 Félicitations ! Vous avez maintenant un compte GitHub.**

---

## 💻 Étape 2 : Installer Git

Git est l'outil en ligne de commande qui permet de gérer vos versions de code localement.

### 2.1 Installation selon votre système d'exploitation

#### 🪟 **Windows**

1. Téléchargez Git depuis [git-scm.com](https://git-scm.com/download/win)
2. Lancez l'installateur
3. **Configuration importante lors de l'installation :**

   - ✅ **Cochez "Git Bash Here"** (permet d'ouvrir un terminal Git depuis n'importe quel dossier)
   - ✅ **Sélectionnez "Use Git from Git Bash only"** ou "Git from the command line and also from 3rd-party software"
   - ✅ **NE PAS installer Git Credential Manager** (décochez cette option)
   - ✅ **Line ending conversion : "Checkout as-is, commit Unix-style line endings"** (conversion automatique CRLF → LF)

4. Cliquez sur **Next** jusqu'à **Install**, puis **Finish**

#### 🍎 **macOS**

1. Ouvrez le **Terminal** (Applications > Utilitaires > Terminal)
2. Tapez la commande :
   ```bash
   xcode-select --install
   ```
3. Cliquez sur **Install** dans la fenêtre qui s'ouvre
4. Acceptez la licence et attendez la fin du téléchargement

### 2.2 Vérification de l'installation

#### Sur Windows :
1. Ouvrez **Git Bash** (clic droit sur le bureau ou dans un dossier → "Git Bash Here")

#### Sur macOS/Linux :
1. Ouvrez le **Terminal**

#### Pour tous :
2. Tapez la commande :
   ```bash
   git --version
   ```
3. Vous devriez voir quelque chose comme : `git version 2.43.0`

**✅ Si vous voyez un numéro de version, Git est correctement installé !**

---

## ⚙️ Étape 2.5 : Configuration globale de Git

Git a besoin de savoir qui vous êtes pour associer vos modifications à votre identité. Cette configuration est **obligatoire**.

### 2.5.1 Configurer votre nom et email

Dans votre terminal (Git Bash sur Windows ou Terminal sur macOS), tapez :

```bash
git config --global user.name "Votre Nom"
git config --global user.email "votre.email@exemple.com"
```

**Remplacez** :
- `"Votre Nom"` par votre nom complet (ex: `"Jean Dupont"`)
- `"votre.email@exemple.com"` par l'email utilisé pour GitHub

**Exemple :**
```bash
git config --global user.name "Jean Dupont"
git config --global user.email "jean.dupont@exemple.com"
```

### 2.5.2 Vérifier la configuration

```bash
git config --global --list
```

Vous devriez voir :
```
user.name=Jean Dupont
user.email=jean.dupont@exemple.com
```

**💡 Vérifiez une dernière fois :**

```bash
git status
```

Vous devriez voir tous vos fichiers en vert, prêts à être commités.

### 12.4 Commiter et pousser

```bash
git commit -m "Ajout du site complet et configuration GitHub Pages"
git push
```

**✅ Tous vos fichiers sont maintenant sur GitHub !**

### 12.5 Vérifier le déploiement

1. Allez sur votre dépôt GitHub
2. Cliquez sur l'onglet **Actions** (en haut)
3. Vous devriez voir votre workflow "Deploy to GitHub Pages" en cours d'exécution (point orange 🟠) ou terminé (coche verte ✅)
4. Cliquez dessus pour voir les détails

**⏳ Attendez que la coche soit verte** (environ 30 secondes à 2 minutes)

### 12.6 Admirer votre site en ligne !

Allez sur : `https://VotreUsername.github.io/mon-portfolio/`

**🎉 FÉLICITATIONS ! Votre site est en ligne !**

---

## 🔄 Workflow quotidien : Mettre à jour votre site

Maintenant que tout est configuré, voici comment mettre à jour votre site :

### Étapes simples

1. **Modifiez** vos fichiers localement dans VS Code
2. **Sauvegardez** vos modifications (`Ctrl + S`)
3. Dans le terminal :
   ```bash
   git add .
   git commit -m "Description de vos modifications"
   git push
   ```
4. **Attendez 1-2 minutes** : GitHub Actions déploie automatiquement
5. **Rafraîchissez** votre site : les modifications sont en ligne !

### Bonnes pratiques pour les messages de commit

Un bon message de commit explique **ce que** vous avez fait et **pourquoi**.

✅ **Bons messages :**
- `"Ajout de la section À propos"`
- `"Correction du bug d'affichage du menu"`
- `"Amélioration du responsive sur mobile"`
- `"Ajout de la page projets avec 3 projets"`

❌ **Mauvais messages :**
- `"Update"`
- `"fix"`
- `"ça marche"`
- `"asdfghjkl"`

**💡 Astuce :** Écrivez votre message comme si vous complétiez la phrase : "Ce commit va..."

---

## 📚 Commandes Git récapitulatives

### Commandes de base

```bash
# Voir l'état actuel (fichiers modifiés, à commiter, etc.)
git status

# Ajouter un fichier spécifique
git add nom-du-fichier.html

# Ajouter tous les fichiers modifiés
git add .

# Commiter avec un message
git commit -m "Votre message"

# Envoyer sur GitHub
git push

# Voir l'historique des commits
git log

# Voir l'historique condensé (une ligne par commit)
git log --oneline

# Voir les différences avant de commiter
git diff
```

### Commandes utiles en cas de problème

```bash
# Annuler les modifications d'un fichier (avant git add)
git checkout -- nom-du-fichier.html

# Retirer un fichier de la staging area (après git add mais avant commit)
git reset nom-du-fichier.html

# Voir les fichiers ignorés par .gitignore
git status --ignored
```

---

## 🎯 Checklist de fin de TP

Vérifiez que vous avez bien accompli toutes les étapes :

- [ ] ✅ Compte GitHub créé
- [ ] ✅ Git installé et configuré (user.name et user.email)
- [ ] ✅ Clé SSH créée et ajoutée à GitHub
- [ ] ✅ Connexion SSH testée et fonctionnelle
- [ ] ✅ Dépôt `mon-portfolio` créé sur GitHub
- [ ] ✅ Dépôt local initialisé et lié à GitHub
- [ ] ✅ README.md créé et poussé
- [ ] ✅ GitHub Pages activé
- [ ] ✅ GitHub Action créée et fonctionnelle
- [ ] ✅ Fichier .gitignore créé
- [ ] ✅ Site complet poussé sur GitHub
- [ ] ✅ Site accessible en ligne à `https://VotreUsername.github.io/mon-portfolio/`

**🎉 Si tout est coché : BRAVO, vous maîtrisez les bases de Git et GitHub Pages !**

---

## 🚨 Problèmes courants et solutions

### Problème 1 : "Permission denied (publickey)"

**Cause :** Votre clé SSH n'est pas correctement configurée.

**Solution :**
1. Vérifiez que la clé est bien ajoutée sur GitHub (Settings → SSH and GPG keys)
2. Retestez la connexion : `ssh -T git@github.com`
3. Si ça ne fonctionne pas, recommencez l'étape 3 (création de clé SSH)

### Problème 2 : "fatal: not a git repository"

**Cause :** Vous n'êtes pas dans un dossier Git ou vous n'avez pas fait `git init`.

**Solution :**
```bash
# Vérifier que vous êtes dans le bon dossier
pwd  # affiche le dossier actuel

# Si besoin, aller dans le bon dossier
cd chemin/vers/votre/projet

# Initialiser Git si pas encore fait
git init
```

### Problème 3 : "Please tell me who you are"

**Cause :** Git n'a pas votre configuration user.name et user.email.

**Solution :**
```bash
git config --global user.name "Votre Nom"
git config --global user.email "votre.email@exemple.com"
```

### Problème 4 : Le site n'affiche pas mon HTML

**Cause :** Votre fichier principal ne s'appelle pas `index.html` ou il n'est pas à la racine.

**Solution :**
1. Renommez votre fichier principal en `index.html`
2. Placez-le à la racine du dépôt
3. Commitez et poussez

### Problème 5 : L'Action GitHub échoue

**Cause :** Plusieurs possibilités (syntaxe YAML incorrecte, permissions manquantes, etc.)

**Solution :**
1. Allez dans l'onglet Actions sur GitHub
2. Cliquez sur le workflow qui a échoué
3. Lisez les logs d'erreur
4. Vérifiez que votre fichier `deploy.yml` est identique à celui du TP
5. Vérifiez que GitHub Pages est bien activé dans Settings → Pages

### Problème 6 : "CRLF will be replaced by LF"

**Cause :** Différence de fin de ligne entre Windows et Unix (c'est normal !).

**Solution :** C'est juste un avertissement, pas une erreur. Git gère ça automatiquement grâce à la configuration faite lors de l'installation. Vous pouvez ignorer ce message.

---

## 🎓 Pour aller plus loin

### Concepts avancés à explorer

Une fois à l'aise avec les bases, vous pourrez apprendre :

1. **Les branches** : Travailler sur plusieurs versions en parallèle
   ```bash
   git branch nouvelle-fonctionnalite
   git checkout nouvelle-fonctionnalite
   ```

2. **Les pull requests** : Proposer des modifications et les faire réviser

3. **Les conflits** : Gérer quand deux personnes modifient le même fichier

4. **Git clone** : Télécharger un projet existant
   ```bash
   git clone git@github.com:username/projet.git
   ```

5. **Les tags** : Marquer des versions spécifiques
   ```bash
   git tag v1.0.0
   ```

### Ressources utiles

- **Documentation Git officielle** : [git-scm.com/doc](https://git-scm.com/doc)
- **GitHub Guides** : [guides.github.com](https://guides.github.com)
- **Formation Git interactive** : [learngitbranching.js.org](https://learngitbranching.js.org/)
- **Aide-mémoire Git** : [training.github.com/downloads/fr/github-git-cheat-sheet](https://training.github.com/downloads/fr/github-git-cheat-sheet/)
- **Pro Git Book (gratuit)** : [git-scm.com/book/fr/v2](https://git-scm.com/book/fr/v2)

### Projets suggérés

Pour pratiquer, essayez de :

1. Créer un second dépôt pour un autre projet
2. Collaborer avec un camarade sur un dépôt commun
3. Contribuer à un projet open source
4. Créer un blog avec Jekyll et GitHub Pages
5. Automatiser d'autres tâches avec GitHub Actions

---

## 📝 Notes importantes à retenir

### Les 3 règles d'or de Git

1. **Commitez souvent** : Mieux vaut 10 petits commits qu'un énorme commit
2. **Messages clairs** : Vos futurs collaborateurs (et votre futur vous) vous remercieront
3. **Testez avant de pousser** : Vérifiez que votre code fonctionne localement

### Sécurité

- 🔒 **Ne commitez JAMAIS** : mots de passe, clés API, tokens, informations personnelles
- 🔒 **Votre clé privée SSH** (`id_ed25519`) ne doit JAMAIS être partagée ou uploadée
- 🔒 Si vous commitez accidentellement un secret, changez-le immédiatement (le simple fait de le supprimer du dépôt ne suffit pas car il reste dans l'historique)

### Philosophie du développement collaboratif

Git et GitHub ne sont pas que des outils techniques, c'est aussi une **culture** :

- 💬 **Communication** : Expliquez vos choix dans les messages de commit
- 🤝 **Collaboration** : Partagez votre code, aidez les autres, contribuez
- 📖 **Documentation** : Un bon README vaut mieux que 1000 commentaires
- 🎨 **Open Source** : Contribuer à des projets libres enrichit toute la communauté

---

## 🎯 Objectifs pédagogiques atteints

À la fin de ce TP, vous devriez être capable de :

- ✅ Expliquer ce qu'est le contrôle de version et pourquoi c'est essentiel
- ✅ Utiliser Git en ligne de commande pour gérer vos projets
- ✅ Créer et gérer des dépôts sur GitHub
- ✅ Comprendre le workflow add → commit → push
- ✅ Publier un site web statique avec GitHub Pages
- ✅ Configurer une GitHub Action pour le déploiement automatique
- ✅ Utiliser .gitignore pour exclure des fichiers
- ✅ Écrire des messages de commit clairs et utiles

---

## 📬 Rendu du TP

Pour valider ce TP, vous devez rendre :

1. **L'URL de votre dépôt GitHub** : `https://github.com/VotreUsername/mon-portfolio`
2. **L'URL de votre site en ligne** : `https://VotreUsername.github.io/mon-portfolio/`
3. **Un screenshot** de l'onglet Actions montrant un déploiement réussi (coche verte ✅)

**Format de rendu :** Envoyez un email avec ces 3 éléments à votre enseignant.

---

## 🎉 Conclusion

Félicitations ! Vous venez de franchir une étape majeure dans votre parcours de développeur. 

Git et GitHub sont utilisés par **des millions de développeurs** dans le monde entier, des étudiants aux ingénieurs des GAFAM. Maîtriser ces outils vous ouvre les portes de la collaboration moderne et du développement professionnel.

**Ce n'est que le début !** Git a encore beaucoup à vous offrir : branches, merges, pull requests, forks, rebase, et bien plus. Mais vous avez maintenant les fondations solides pour construire là-dessus.

> "Code is like humor. When you have to explain it, it's bad."  
> — Cory House

Mais contrairement au code, **l'historique Git doit toujours être explicite** ! 😉

**Bon développement et bonne continuation ! 🚀**

---

## 📎 Annexes

### Annexe A : Aide-mémoire Git (à imprimer)

```
┌──────────────────────────────────────────────────────┐
│             COMMANDES GIT ESSENTIELLES               │
├──────────────────────────────────────────────────────┤
│ CONFIGURATION                                        │
│ git config --global user.name "Nom"                  │
│ git config --global user.email "email@exemple.com"   │
│                                                      │
│ INITIALISATION                                       │
│ git init                    Créer un dépôt           │
│ git clone <url>             Cloner un dépôt          │
│                                                      │
│ MODIFICATIONS                                        │
│ git status                  Voir l'état              │
│ git add <fichier>           Ajouter un fichier       │
│ git add .                   Ajouter tous les fichiers│
│ git commit -m "message"     Commiter                 │
│ git push                    Pousser sur GitHub       │
│                                                      │
│ INFORMATION                                          │
│ git log                     Historique complet       │
│ git log --oneline           Historique condensé      │
│ git diff                    Voir les différences     │
│                                                      │
│ ANNULATION                                           │
│ git checkout -- <fichier>   Annuler modifications    │
│ git reset <fichier>         Retirer du staging       │
└──────────────────────────────────────────────────────┘
```

### Annexe B : Syntaxe Markdown

```markdown
# Titre 1
## Titre 2
### Titre 3

**Gras**
*Italique*
***Gras et italique***

- Liste
- À puces

1. Liste
2. Numérotée

[Lien](https://exemple.com)
![Image](url-image.jpg)

`code inline`

```
Bloc de code
```

> Citation

---
Ligne horizontale
```

### Annexe C : Structure d'un bon projet web

```
mon-portfolio/
├── .github/
│   └── workflows/
│       └── deploy.yml
├── .gitignore
├── README.md
├── index.html
├── css/
│   └── style.css
├── js/
│   └── script.js
├── images/
│   ├── photo.jpg
│   └── logo.png
└── pages/
    ├── about.html
    └── contact.html
```

---

## 📚 Sources et références

### Documentation officielle

1. **Git Documentation** - [git-scm.com/doc](https://git-scm.com/doc)
   - Documentation complète de Git, tutoriels et références des commandes

2. **GitHub Docs** - [docs.github.com](https://docs.github.com)
   - Documentation officielle de GitHub, guides et API

3. **GitHub Pages Documentation** - [docs.github.com/pages](https://docs.github.com/pages)
   - Guide complet pour publier des sites avec GitHub Pages

4. **GitHub Actions Documentation** - [docs.github.com/actions](https://docs.github.com/actions)
   - Documentation sur l'automatisation avec GitHub Actions

### Livres et ressources pédagogiques

5. **Pro Git Book** par Scott Chacon et Ben Straub - [git-scm.com/book](https://git-scm.com/book/fr/v2)
   - Livre complet sur Git, disponible gratuitement en ligne en français

6. **GitHub Skills** - [skills.github.com](https://skills.github.com)
   - Cours interactifs gratuits proposés par GitHub

7. **Learn Git Branching** - [learngitbranching.js.org](https://learngitbranching.js.org/)
   - Tutoriel interactif pour apprendre Git de manière ludique

### Guides et tutoriels

8. **Atlassian Git Tutorials** - [atlassian.com/git/tutorials](https://www.atlassian.com/git/tutorials)
   - Tutoriels détaillés sur Git par l'équipe Atlassian (Bitbucket)

9. **Git Cheat Sheet** par GitHub - [training.github.com/downloads/](https://training.github.com/downloads/fr/github-git-cheat-sheet/)
   - Aide-mémoire des commandes Git essentielles

10. **Markdown Guide** - [markdownguide.org](https://www.markdownguide.org)
    - Guide complet de la syntaxe Markdown

### Articles et concepts

11. **Understanding the GitHub Flow** - [guides.github.com/introduction/flow](https://guides.github.com/introduction/flow/)
    - Comprendre le workflow collaboratif sur GitHub

12. **Git - the simple guide** par Roger Dudler - [rogerdudler.github.io/git-guide](https://rogerdudler.github.io/git-guide/index.fr.html)
    - Guide simple de Git en français

13. **SSH Protocol** - [ssh.com/academy/ssh](https://www.ssh.com/academy/ssh)
    - Documentation sur le protocole SSH

### Outils et extensions

14. **Visual Studio Code Git Integration** - [code.visualstudio.com/docs/sourcecontrol/overview](https://code.visualstudio.com/docs/sourcecontrol/overview)
    - Documentation sur l'intégration Git dans VS Code

15. **GitLens Extension** - [gitlens.amod.io](https://gitlens.amod.io)
    - Extension VS Code pour visualiser l'historique Git

### Concepts de sécurité

16. **GitHub Security Best Practices** - [docs.github.com/security](https://docs.github.com/en/code-security)
    - Guide des bonnes pratiques de sécurité sur GitHub

17. **Removing sensitive data from a repository** - [docs.github.com/authentication/keeping-your-account-and-data-secure/removing-sensitive-data-from-a-repository](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/removing-sensitive-data-from-a-repository)
    - Guide pour supprimer des données sensibles d'un dépôt

### Communauté et support

18. **Stack Overflow - Git Questions** - [stackoverflow.com/questions/tagged/git](https://stackoverflow.com/questions/tagged/git)
    - Forum de questions/réponses sur Git

19. **GitHub Community Forum** - [github.community](https://github.community)
    - Forum communautaire GitHub

20. **Git mailing list** - [git.vger.kernel.org](https://git.vger.kernel.org)
    - Liste de diffusion officielle de Git

---

**Version du document : 2.0**  
**Dernière mise à jour : Janvier 2026**  
**Licence : CC BY-SA 4.0** Pourquoi c'est important ?** Chaque modification que vous enregistrez dans Git sera signée avec ces informations. C'est comme signer un document officiel.

---

## 🔐 Étape 3 : Créer une clé SSH

SSH est un protocole sécurisé qui permet de s'authentifier sur GitHub sans avoir à taper son mot de passe à chaque fois.

### 3.1 Qu'est-ce qu'une clé SSH ?

Une clé SSH fonctionne comme une **paire de clés physiques** :
- 🔑 **Clé privée** (`id_ed25519`) : Reste sur votre ordinateur, ne doit JAMAIS être partagée
- 🔓 **Clé publique** (`id_ed25519.pub`) : Peut être partagée, vous la donnez à GitHub

C'est comme une serrure (GitHub) et une clé (votre ordinateur). Seule votre clé peut ouvrir cette serrure.

### 3.2 Générer votre paire de clés

Dans votre terminal, tapez :

```bash
ssh-keygen -t ed25519 -C "votre.email@exemple.com"
```

**Remplacez** `votre.email@exemple.com` par votre email GitHub.

Vous verrez :
```
Generating public/private ed25519 key pair.
Enter file in which to save the key (/home/user/.ssh/id_ed25519):
```

1. **Appuyez sur Entrée** (pour accepter l'emplacement par défaut)
2. Quand on vous demande un mot de passe (*passphrase*) :
   ```
   Enter passphrase (empty for no passphrase):
   ```
   **Appuyez sur Entrée** (pas de mot de passe pour simplifier)
3. Confirmez en appuyant à nouveau sur **Entrée**

Vous verrez un message de confirmation avec un "randomart" (dessin ASCII).

**✅ Votre paire de clés SSH est créée !**

Les fichiers sont dans le dossier `~/.ssh/` :
- `~/.ssh/id_ed25519` : votre clé privée (🔒 SECRÈTE)
- `~/.ssh/id_ed25519.pub` : votre clé publique (📢 partageable)

---

## 📤 Étape 4 : Ajouter la clé SSH à GitHub

### 4.1 Afficher votre clé publique

Dans votre terminal, tapez :

#### Sur macOS/Linux et Windows (Git Bash) :
```bash
cat ~/.ssh/id_ed25519.pub
```

Vous verrez quelque chose comme :
```
ssh-ed25519 AAAAC3NzaC1lZDI1NTE5AAAAIGzT... votre.email@exemple.com
```

### 4.2 Copier la clé

**Sélectionnez TOUT le texte affiché** (de `ssh-ed25519` jusqu'à votre email) et copiez-le :
- Windows (Git Bash) : Sélectionnez avec la souris, puis clic droit → Copy
- macOS : Sélectionnez avec la souris, puis Cmd+C
- Linux : Sélectionnez avec la souris, puis Ctrl+Shift+C

**⚠️ Important** : Copiez TOUTE la ligne, y compris `ssh-ed25519` au début et votre email à la fin.

### 4.3 Ajouter la clé sur GitHub

1. Allez sur [github.com](https://github.com) et connectez-vous
2. Cliquez sur votre **photo de profil** (en haut à droite)
3. Sélectionnez **Settings** (Paramètres)
4. Dans le menu de gauche, cliquez sur **SSH and GPG keys**
5. Cliquez sur le bouton vert **New SSH key**
6. Remplissez le formulaire :
   - **Title** : Donnez un nom descriptif, par exemple : `PC personnel` ou `Mac IUT`
   - **Key** : Collez votre clé publique copiée précédemment
7. Cliquez sur **Add SSH key**
8. GitHub peut vous demander votre mot de passe pour confirmer

**✅ Votre clé SSH est maintenant ajoutée à GitHub !**

---

## 🔗 Étape 5 : Tester la connexion SSH

Avant d'aller plus loin, vérifions que la connexion entre votre ordinateur et GitHub fonctionne.

### 5.1 Tester la connexion

Dans votre terminal, tapez :

```bash
ssh -T git@github.com
```

**La première fois**, vous verrez un message comme :
```
The authenticity of host 'github.com (140.82.121.4)' can't be established.
ED25519 key fingerprint is SHA256:+DiY3wvvV6TuJJhbpZisF/zLDA0zPMSvHdkr4UvCOqU.
Are you sure you want to continue connecting (yes/no/[fingerprint])?
```

**Tapez `yes` et appuyez sur Entrée.**

Vous devriez ensuite voir :
```
Hi VotreUsername! You've successfully authenticated, but GitHub does not provide shell access.
```

**✅ Parfait ! La connexion SSH fonctionne.**

**❌ Si vous avez une erreur :**
- Vérifiez que vous avez bien copié toute la clé publique
- Vérifiez que la clé est bien ajoutée dans les paramètres GitHub
- Recommencez depuis l'étape 3 si nécessaire

---

## 📦 Étape 6 : Comprendre Git et les dépôts

Avant de créer votre premier dépôt, comprenons les concepts de base.

### 6.1 Qu'est-ce qu'un dépôt (repository) ?

Un **dépôt** (ou *repository*, souvent abrégé *repo*) est un dossier qui contient :
- 📁 Vos fichiers de projet (HTML, CSS, images, etc.)
- 📜 L'historique complet de toutes les modifications
- ⚙️ Des fichiers de configuration Git (dans le dossier caché `.git/`)

### 6.2 Public vs Private

Quand vous créez un dépôt sur GitHub, vous choisissez sa visibilité :

- **🌍 Public** : Tout le monde peut voir votre code (mais seuls vous et vos collaborateurs peuvent le modifier)
  - ✅ Idéal pour des projets open source, portfolios, partage de connaissances
  - ✅ Gratuit sans limitation
  
- **🔒 Private** : Seuls vous et les personnes que vous invitez peuvent voir le code
  - ✅ Idéal pour des projets professionnels, clients, code sensible
  - ✅ Gratuit sur GitHub (limité avant, maintenant illimité)

### 6.3 Le fichier README.md

Le **README.md** est la "page d'accueil" de votre dépôt. C'est la première chose que les visiteurs voient.

Il est écrit en **Markdown**, un langage de mise en forme simple :

```markdown
# Mon Portfolio

Ceci est mon site web personnel créé en BUT Informatique.

## Technologies utilisées

- HTML5
- CSS3
- GitHub Pages

## Auteur

Jean Dupont - Étudiant en BUT Informatique
```

**Le `.md` signifie Markdown.**

### 6.4 Les commandes Git essentielles

Voici les commandes que nous allons utiliser aujourd'hui :

| Commande | Description |
|----------|-------------|
| `git init` | Initialise un nouveau dépôt Git dans le dossier actuel |
| `git add <fichier>` | Prépare un fichier pour être enregistré (*staging*) |
| `git add .` | Prépare TOUS les fichiers modifiés |
| `git commit -m "message"` | Enregistre les modifications avec un message descriptif |
| `git push` | Envoie vos commits locaux vers GitHub |
| `git status` | Affiche l'état actuel de votre dépôt |
| `git log` | Affiche l'historique des commits |

### 6.5 Le workflow Git de base

Voici le cycle de travail avec Git :

```
1. Modifier vos fichiers
   ↓
2. git add . (préparer les modifications)
   ↓
3. git commit -m "Description" (enregistrer localement)
   ↓
4. git push (envoyer sur GitHub)
   ↓
5. Vos modifications sont en ligne ! 🎉
```

**💡 Analogie :** 
- `git add` = Mettre des colis dans un chariot
- `git commit` = Emballer le chariot avec une étiquette
- `git push` = Envoyer le colis à la poste (GitHub)

---

## 🚀 Étape 7 : Créer votre dépôt "mon-portfolio"

### 7.1 Créer le dépôt sur GitHub

1. Allez sur [github.com](https://github.com)
2. Cliquez sur le **+** en haut à droite, puis **New repository**
3. Remplissez le formulaire :
   - **Repository name** : `mon-portfolio`
   - **Description** : `Mon site web personnel - BUT Informatique` (optionnel mais recommandé)
   - **Public** : ✅ Cochez (pour que GitHub Pages fonctionne gratuitement)
   - **Initialize this repository with** : ❌ Ne cochez RIEN (ni README, ni .gitignore, ni license)
4. Cliquez sur **Create repository**

**✅ Votre dépôt est créé !**

### 7.2 Page d'instructions

GitHub vous montre maintenant une page avec des instructions. **Ne fermez pas cette page**, nous allons utiliser ces commandes.

Vous devriez voir une section "…or create a new repository on the command line" avec des commandes comme :

```bash
echo "# mon-portfolio" >> README.md
git init
git add README.md
git commit -m "first commit"
git branch -M main
git remote add origin git@github.com:VotreUsername/mon-portfolio.git
git push -u origin main
```

**💡 Gardez cette page ouverte, nous allons utiliser ces commandes.**

---

## 🔧 Étape 8 : Initialiser Git localement

### 8.1 Ouvrir votre projet dans VS Code

1. Ouvrez **Visual Studio Code**
2. Ouvrez le dossier contenant votre site web (Fichier → Ouvrir le dossier...)
3. Ouvrez un terminal intégré dans VS Code :
   - Menu : **Terminal → Nouveau terminal**
   - Ou raccourci : `Ctrl + ù` (Windows) / `Cmd + ù` (Mac)

**Sur Windows**, assurez-vous d'utiliser **Git Bash** :
- Si le terminal affiche `PS` (PowerShell), cliquez sur la flèche vers le bas à côté du **+** et sélectionnez **Git Bash**

### 8.2 Initialiser le dépôt Git

Dans le terminal VS Code, tapez :

```bash
git init
```

Vous verrez : `Initialized empty Git repository in ...`

**✅ Git est maintenant actif dans ce dossier !**

### 8.3 Configurer l'origine (remote)

Retournez sur la page GitHub de votre dépôt vide. Copiez la ligne qui ressemble à :

```bash
git remote add origin git@github.com:VotreUsername/mon-portfolio.git
```

**⚠️ IMPORTANT** : Assurez-vous que l'URL commence par `git@github.com:` et pas par `https://`. C'est l'URL SSH qui utilise votre clé.

Collez cette commande dans votre terminal VS Code et appuyez sur **Entrée**.

### 8.4 Définir la branche principale

```bash
git branch -M main
```

Cela renomme votre branche par défaut en `main` (c'est la convention moderne sur GitHub).

**✅ Votre dépôt local est maintenant lié à GitHub !**

---

## 📝 Étape 9 : Créer et publier un README

### 9.1 Comprendre le Markdown

Le **Markdown** est un langage de mise en forme ultra-simple. Voici les bases :

```markdown
# Titre de niveau 1 (le plus grand)
## Titre de niveau 2
### Titre de niveau 3

**texte en gras**
*texte en italique*

- Liste à puces
- Deuxième élément
- Troisième élément

1. Liste numérotée
2. Deuxième élément
3. Troisième élément

[Lien cliquable](https://www.exemple.com)

![Texte alternatif pour une image](url-de-l-image.jpg)

`code inline`

```
Code sur
plusieurs lignes
```
```

### 9.2 Créer votre README.md

Dans VS Code :

1. Créez un nouveau fichier : **Fichier → Nouveau fichier**
2. Sauvegardez-le avec le nom : `README.md` (attention aux majuscules !)
3. Écrivez votre contenu. Exemple :

```markdown
# Mon Portfolio

Bienvenue sur mon site web personnel !

## À propos

Je suis étudiant en première année de BUT Informatique.  
Ce site présente mes projets et mes compétences en développement web.

## Technologies utilisées

- HTML5
- CSS3
- GitHub Pages

## Auteur

**Votre Nom**  
Étudiant en BUT Informatique - Promotion 2024
```

4. Sauvegardez le fichier (`Ctrl + S` ou `Cmd + S`)

### 9.3 Premier commit et push

Dans le terminal VS Code, tapez les commandes suivantes **une par une** :

```bash
git add README.md
```

Cette commande prépare le fichier README.md pour être enregistré.

```bash
git commit -m "Ajout du fichier README"
```

Cette commande enregistre le fichier avec un message descriptif.

```bash
git push -u origin main
```

Cette commande envoie votre commit sur GitHub.

**La première fois**, vous verrez beaucoup de texte défiler. À la fin, vous devriez voir :
```
To github.com:VotreUsername/mon-portfolio.git
 * [new branch]      main -> main
```

**✅ Votre README est maintenant en ligne !**

### 9.4 Vérifier sur GitHub

1. Retournez sur la page de votre dépôt sur GitHub (rechargez la page)
2. Vous devriez voir votre fichier `README.md` affiché avec la mise en forme Markdown !

### 9.5 Modifier et pousser à nouveau

Maintenant, modifions le README pour comprendre le cycle complet.

1. Dans VS Code, modifiez votre `README.md`, par exemple ajoutez une section :
   ```markdown
   ## Contact
   
   - Email : votre.email@exemple.com
   - GitHub : [@VotreUsername](https://github.com/VotreUsername)
   ```

2. Sauvegardez (`Ctrl + S`)

3. Dans le terminal, tapez :
   ```bash
   git add README.md
   git commit -m "Ajout de la section Contact"
   git push
   ```

4. Retournez sur GitHub et rechargez la page : vos modifications sont en ligne !

**💡 Vous avez compris le workflow Git ! C'est toujours : `add → commit → push`**

---

## 🌐 Étape 10 : Activer GitHub Pages

GitHub Pages permet de transformer votre dépôt en site web accessible publiquement.

### 10.1 Activer Pages

1. Sur GitHub, allez sur votre dépôt `mon-portfolio`
2. Cliquez sur **Settings** (Paramètres) en haut
3. Dans le menu de gauche, cliquez sur **Pages**
4. Dans la section **Source** :
   - **Branch** : Sélectionnez `main`
   - **Folder** : Laissez `/ (root)`
5. Cliquez sur **Save**

Vous verrez un message : "Your site is ready to be published at https://VotreUsername.github.io/mon-portfolio/"

**⏳ Attendez 1-2 minutes**, puis rafraîchissez la page. Le message deviendra : "Your site is live at ..."

**✅ GitHub Pages est activé !**

### 10.2 Vérifier

Cliquez sur le lien ou allez sur `https://VotreUsername.github.io/mon-portfolio/`

Vous devriez voir... **uniquement votre README pour l'instant** (GitHub Pages affiche le README.md par défaut si vous n'avez pas d'`index.html`).

---

## ⚙️ Étape 11 : Ajouter une GitHub Action pour le déploiement

Les **GitHub Actions** sont des automatisations qui s'exécutent sur GitHub. Ici, nous allons créer une action qui déploie automatiquement votre site à chaque fois que vous poussez du code.

### 11.1 Qu'est-ce qu'une GitHub Action ?

Une GitHub Action est un **robot automatique** qui exécute des tâches pour vous. Par exemple :
- ✅ Tester votre code automatiquement
- ✅ Déployer votre site web
- ✅ Envoyer des notifications
- ✅ Compiler votre code

**Notre action** va :
1. Détecter quand vous poussez du code sur la branche `main`
2. Prendre tous vos fichiers
3. Les envoyer sur GitHub Pages
4. Votre site est mis à jour automatiquement ! 🎉

### 11.2 Créer le dossier pour les workflows

Dans VS Code :

1. Créez un nouveau dossier `.github` à la racine de votre projet
   - **Important** : le nom commence par un point `.`
2. Dans ce dossier `.github`, créez un sous-dossier `workflows`

Votre arborescence doit ressembler à :
```
mon-portfolio/
├── .github/
│   └── workflows/
├── README.md
├── index.html (votre site)
├── style.css
└── ...
```

### 11.3 Créer le fichier de workflow

1. Dans le dossier `.github/workflows/`, créez un nouveau fichier nommé `deploy.yml`
2. Copiez-collez ce contenu :

```yaml
name: Deploy to GitHub Pages

on:
  push:
    branches:
      - main

jobs:
  deploy:
    runs-on: ubuntu-latest
    environment: github-pages
    permissions:
      contents: read
      pages: write
      id-token: write
    steps:
      - name: Checkout
        uses: actions/checkout@v6
      - name: Setup Pages
        uses: actions/configure-pages@v4
      - name: Upload artifact
        uses: actions/upload-pages-artifact@v4
        with:
          path: .
      - name: Deploy to GitHub Pages
        id: deployment
        uses: actions/deploy-pages@v4
```

3. Sauvegardez le fichier

### 11.4 Comprendre le fichier (optionnel)

- **name** : Le nom de l'action
- **on: push: branches: - main** : L'action se déclenche quand vous poussez sur `main`
- **jobs** : Les tâches à exécuter
- **runs-on: ubuntu-latest** : L'action s'exécute sur un serveur Linux
- **steps** : Les étapes de déploiement (checkout du code, configuration, upload, déploiement)

**⚠️ Important sur le `path`** :

Dans la section `Upload artifact`, il y a `path: .`

- `path: .` signifie : "Prends TOUT à la racine du dépôt"
- Si votre site était dans un sous-dossier `site/`, vous mettriez `path: site`

**Pour ce TP, laissez `path: .` car votre site est à la racine.**

---

## 📤 Étape 12 : Pousser votre site complet

### 12.1 Le fichier .gitignore

Avant de pousser tous vos fichiers, créons un fichier `.gitignore`.

#### Qu'est-ce que .gitignore ?

Le fichier `.gitignore` liste les fichiers et dossiers que Git doit **ignorer**. C'est essentiel pour :
- ❌ Ne pas envoyer des fichiers temporaires
- ❌ Ne pas envoyer des fichiers système (`.DS_Store` sur Mac, `Thumbs.db` sur Windows)
- ❌ Ne pas envoyer des fichiers de configuration locaux
- ❌ Ne pas envoyer des gros fichiers inutiles

#### Créer le .gitignore

1. Dans VS Code, créez un fichier `.gitignore` à la racine
2. Ajoutez ce contenu :

```
# Fichiers système
.DS_Store
Thumbs.db
Desktop.ini

# Fichiers VS Code (optionnel)
.vscode/

# Fichiers temporaires
*.tmp
*.log
*~

# Node modules (si vous utilisez npm plus tard)
node_modules/

# Fichiers de sauvegarde
*.bak
*.swp
```

3. Sauvegardez

**✅ Git ignorera maintenant ces fichiers automatiquement !**

### 12.2 Vérifier les fichiers à envoyer

Avant de tout pousser, vérifions ce qui va être envoyé :

```bash
git status
```

Vous devriez voir :
- ✅ Vos fichiers HTML, CSS
- ✅ Vos images
- ✅ README.md
- ✅ .github/workflows/deploy.yml
- ✅ .gitignore

Vous ne devriez **PAS** voir :
- ❌ Fichiers système (.DS_Store, etc.)
- ❌ Fichiers de configuration éditeur

Si vous voyez des fichiers indésirables, ajoutez-les dans `.gitignore` !

### 12.3 Ajouter tous les fichiers

```bash
git add .
```

Le point `.` signifie "tous les fichiers" (sauf ceux dans .gitignore).

### 12.4 Committer les modifications

```bash
git commit -m "Ajout du site complet avec GitHub Action"
```
### 12.5 Pousser sur GitHub

```bash
git push
```
### 12.6 Vérifier le déploiement
1. Allez sur votre dépôt GitHub
2. Cliquez sur l'onglet **Actions**
3. Vous devriez voir votre workflow "Deploy to GitHub Pages" en cours d'exécution
4. Attendez que l'action se termine (cela peut prendre quelques minutes)
5. Une fois terminé, retournez sur `https://VotreUsername.github.io/mon-portfolio/` et rafraîchissez la page
Vous devriez voir votre site web complet en ligne !

**✅ Félicitations ! Votre site est maintenant en ligne avec déploiement automatique via GitHub Actions !**

### 12.7 Bonus : Régler le lien vers votre site dans la page GitHub
1. Cliquez sur l'engrenage à proximité de "About" dans votre dépôt GitHub
2. Cliquez sur la checkbox "Use your GitHub Pages website"

-- (c) Ronan Le Meillat - SCTG Development - 2025
