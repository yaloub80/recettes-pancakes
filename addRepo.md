1. Cloner le dépôt O’clock (repo source)
git clone git@github.com/O-clock-Trinity/NomDuRepo
cd NomDuRepo

2. Récupérer toutes les branches distantes
for BRANCH in $(git branch -a | grep remotes | grep -v HEAD | grep -v master); do \
git branch --track "${BRANCH#remotes/origin/}" "${BRANCH}"; \
done

3. Supprimer le README.md de chaque branche
for BRANCH in $(git branch); do \
git checkout ${BRANCH} && \
git filter-branch -f --index-filter 'git rm --cached --ignore-unmatch README.md'; \
done

4. Changer la remote vers ton propre repo

Supprime l’ancienne remote :
git remote remove origin

Ajoute ton nouveau repo (ex : git@github.com/yaloub80/mon-projet.git) :
git remote add origin git@github.com/yaloub80/mon-projet.git

Push toutes les branches sur ton GitHub
git push --all

Et si le repo contient des tags :
git push --tags

README.md a ajouté 
# Recette Pancakes (Challenge O'clock)
Ce repo est une copie d'un challenge fourni par l'école O'clock.
Les énoncés ont été retirés (README.md supprimés de toutes les branches).



