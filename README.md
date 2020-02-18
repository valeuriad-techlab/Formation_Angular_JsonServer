
# JsonServer
Permet d'avoir un serveur local qu'on peut requête tel une API

# Mise en place
https://github.com/typicode/json-server
https://appdividend.com/2019/06/06/angular-8-httpclient-example-how-to-send-ajax-request-in-angular/

# Pour générer une API avec des résulats random
https://egghead.io/lessons/javascript-creating-demo-apis-with-json-server


# install
Installer JSON Server : (Permet de simuler une API REST)
`npm install -g json-server` ou `yarn global add json-server`

# Contenu de notre API
Création d’un dossier (Pas d’emplacement spécifique)
Création d’un fichier “db.json” avec le contenu suivant :(Ne pas changer le nom du fichier)
<code>{
  "users": [],
  "articles": []
}
</code>
Lancer la commande: (à l’emplacement du fichier “db.json”)

    json-server --watch db.json

| Route | Description |
|--|--|
| GET /users ou /articles | Liste les utilisateurs ou Articles |
| GET /users ou /articles et /1 | Détail d’un utilisateur ou Article |
| POST /users ou /articles | Ajoute un utilisateur ou Article |
| PUT /users ou /articles et /1 | Modifie un utilisateur ou Article |
| PATCH /users ou /articles et /1 | Modifie une propriété d’un utilisateur ou Article |
| DELETE /users ou /articles et /1 | Supprime un utilisateur ou Article |


# Aller plus loin avec Json-Serve

Lancer la commande suivante à la racine de l’installation de json-serve
Il doit se trouver dans "C:\Users\<VOUS>\AppData\Roaming\npm"

    npm install faker lodash
Dans votre dossier qui contient le fichier “db.json”.
Créer un fichier “generate.js” avec le contenu suivant

    module.exports = function(){
	    var faker = require("faker");
	    var _ = require("lodash");
	    return {
	      people: _.times(100,function(n) {
	        return {
	          id: n,
	          name: faker.name.findName(),
	          avatar: faker.internet.avatar()
	        }
	      })
	    }
    }
Puis lancer la commande suivante :

    json-server --watch generate.js
Vous avez maintenant une liste de 100 personnes accessibles à l’adresse http://localhost:3000/people
