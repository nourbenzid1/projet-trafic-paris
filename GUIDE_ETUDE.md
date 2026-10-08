# Guide d'étude (fichier personnel : ne pas pousser sur GitHub si le dépôt est évalué)

Ordre conseillé : lire chaque notebook, **exécuter cellule par cellule**, et essayer de prédire la sortie avant de lancer.

## Les idées à maîtriser, notebook par notebook
**01 – Chargement**
- Pourquoi regarder le fichier brut avant `read_csv` ? (séparateur, BOM, dates)
- `dtype` : pourquoi un identifiant est un `string` et pas un nombre ? À quoi sert `category` ?
- `chunksize` : quand est-ce indispensable ?

**02 – Nettoyage**
- `to_datetime(utc=True)` puis `tz_convert` : pourquoi dans cet ordre ? Que se passe-t-il le 29 mars ?
- Doublon complet vs doublon sur la clé `(iu_ac, t_1h)`.
- Supprimer, imputer ou laisser `NaN` : les arguments pour chaque option.
- Pourquoi `Inconnu` n'est pas un état ?

**03 – Transformation**
- Variables temporelles (`dt.hour`, `dt.dayofweek`), `pd.cut`.
- Ordinal vs one-hot : pourquoi ne pas coder `axe` en 0/1/2 ?
- Valeurs aberrantes : règle métier vs règle IQR, pourquoi *par tronçon* ?
- `groupby(...).agg(...)` : moyenne, médiane, écart-type.

**04 – Analyse**
- Profil horaire, heatmap (`pivot_table`), diagramme fondamental.
- Comment passer d'un graphique à une phrase d'interprétation chiffrée.

## Questions d'auto-test
1. Que devient la moyenne de `q` si on garde les 60 000 véh/h aberrants ? Et la médiane ?
2. Pourquoi ne pas remplacer les `NaN` de `k` par la moyenne ?
3. Qu'est-ce qui change si on oublie `utc=True` ?
4. Pourquoi les jours fériés sont-ils regroupés avec le week-end ?
5. Que montre le sommet de la « cloche » du diagramme fondamental ?

## Exercices pour aller plus loin
- Changer les axes dans `ROUTES` et relancer tout.
- Ajouter une carte ou comparer avant/pendant vacances d'été.
- Remplacer le seuil `3 × IQR` par `1,5 × IQR` et regarder l'effet sur les statistiques.
