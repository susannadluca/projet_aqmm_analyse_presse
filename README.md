Projet AQMM - Analyse quantitative et modélisation thématique de la presse française (1950–1970) 
Master 2 Humanités Numériques – École des Chartes – Janvier 2026 Autrice : Susanna De Luca Contact : susanna.de.luca@chartes.psl.eu

Ce projet s’inscrit dans une réflexion plus large sur l’évolution du discours médiatique en France durant l’après-guerre. L’objectif est d’examiner comment les journaux français ont structuré, sélectionné et formulé l’information entre les années 1950 et 1970, période marquée par des transformations sociales, politiques et culturelles majeures.

Pour répondre à ces questions, j’ai mobilisé un ensemble de méthodes quantitatives afin d’examiner simultanément le lexique, les thèmes et les structures sémantiques du corpus.

Le corpus provient du jeu de données French Public Domain Newspapers disponible sur Hugging Face.

J’ai constitué un sous-corpus équilibré de 300 articles, répartis équitablement entre les années 1950, 1960 et 1970.
Après une phase de nettoyage et de contrôle de qualité, le corpus final comprend 292 articles, chacun accompagné: de l’année exacte extraite automatiquement malgré les imperfections OCR, de la décennie correspondante; du texte nettoyé utilisé pour les analyses.

Le repository contient soit le corpus initial, soit le corpus enrichi après les traitements et la modélisation thématique.

Approche méthodologique:
L’analyse repose sur une chaîne de traitement entièrement reproductible, développée en Python.
Elle commence par un nettoyage linguistique classique (minuscules, suppression de la ponctuation, élimination des symboles OCR récurrents, retrait des stopwords), puis par une vectorisation en TF–IDF, choisie pour sa robustesse sur des textes courts ou bruités.
Sur cette base, j’ai entraîné un modèle NMF (10 topics), particulièrement adapté aux matrices TF–IDF et plus stable que LDA pour ce type de données.
Le modèle produit des thèmes interprétables à partir de listes pondérées de mots, ainsi que des scores thématiques pour chaque article.
J’ai ensuite analysé la distribution de ces thèmes dans le temps afin d’observer les évolutions d’une décennie à l’autre.
Enfin, une analyse de co-occurrences lexicale a permis d’explorer la structure sémantique globale du corpus, en identifiant les nœuds centraux et les principales communautés lexicales.

Principaux résultats:
L’analyse montre que le corpus contient des thématiques couvrant un spectre très varié : administration municipale, politique sociale, aviation, religion, mouvements sportifs, économie internationale, etc.
Certaines thématiques révèlent une continuité forte sur les trois décennies, tandis que d’autres évoluent nettement selon le contexte historique (modernisation, Guerre froide, transformations institutionnelles, montée des loisirs).
La modélisation NMF met également en lumière un thème culturel littéraire lié à Péguy, un thème socio-politique, un thème religieux, un thème sportif et un thème administratif. L’analyse temporelle montre que certains topics deviennent plus présents à partir des années 1960, tandis que d’autres déclinent ou restent stables.
La structure du réseau de co-occurrences — relativement dense mais faiblement modularisée — reflète le caractère hétérogène du corpus, composé d’articles courts sur des sujets très divers mais partageant un vocabulaire institutionnel commun.

L’ensemble du travail a été réalisé sous Python (Google Colab) en utilisant: pandas et numpy pour le traitement des données, regex pour l’extraction automatique des années, nltk pour les stopwords, scikit-learn pour TF–IDF et NMF, matplotlib et seaborn pour les graphiques, networkx pour les analyses de réseaux.

Ces outils permettent une analyse reproductible et conforme à l’esprit du cours : une modélisation mathématique appliquée à des données textuelles de sciences humaines.

Limites: Le corpus reste restreint (292 articles) et comporte du bruit lié à l’OCR, ce qui limite la finesse de certaines analyses. La modélisation thématique via TF–IDF + NMF reste une approche bag-of-words, insensible à la syntaxe, aux relations profondes ou aux connotations. Une analyse plus avancée nécessiterait des embeddings contextuels ou un corpus plus vaste et homogène.

Ce travail pourrait être prolongé en : élargissant le corpus à d’autres années ou à d’autres titres, appliquant des méthodes modernes de représentation sémantique (BERT, word2vec), comparant l’évolution du discours français avec celle d’autres pays, intégrant cette analyse dans la problématique de mon mémoire sur les transformations culturelles et discursives post-guerre.
