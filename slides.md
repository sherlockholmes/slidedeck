% title: Change Log MongoDB 3.0
% subtitle: WiredTiger y más
% author: Raul Hugo
% author: Otro maestro del tiempo.
% thankyou: Gracias totales.
% thankyou_details: MongoDB Peru - AWS PERU
% contact: <span>Sitio Web</span> <a href="http://aws.pe/">aws.pe</a>
% contact: <span>Github</span> <a href="http://github.com/sherlockholmes">sherlockholmes</a>
% favicon: https://media.mongodb.org/favicon.ico 

---
title: Issues comunes en MongoDB 2.x
class: img-top-center
build_lists: true

<img height=250 src=figures/writelock.jpg />

MongoDB 2.x tuvo los siguientes problemas comunes:

- Global Write lock -> Bloqueo Global de Escritura. 
- Preallocation white spaces. Reserva de Espacios en Blanco. 
- Mongo Credentials Encriptamiento Inseguro.



---
title: Wired Tiger
subtitle: El Nuevo Motor

- Nuevo Motor añadido en Mongodb 3.0
Fetures:
- Locking a nivel de documento ya no global.
- Tres Niveles de Compresion por Defecto.
- Corrige alguna falencias de MMAPv1

<footer class="source"> https://www.youtube.com/watch?feature=player_embedded&v=O9TGqK3FBX8 </footer>

---
title: Credenciales de MongoDB
subtitle: El nuevo SCRAM-SHA
class: segue dark nobackground

---
title: Autenticación  

Hasta la version 2.6 mongodb usaba autenticacion basada en un encriptamiento propio llamado mongo credentials.

<pre class="prettyprint" data-lang="json">
{
	"_id" : "admin.usr_admin_mdb",
	"user" : "usr_admin_mdb",
	"db" : "admin",
	"credentials" : {
<b>		"SCRAM-SHA-1" : { </b>
			"iterationCount" : 10000,
			"salt" : "C/3yWPKoIhr8mvRPFcy32==",
			"storedKey" : "ZIU0xkE2MMukq0JD6564g4LhmGEP6E=",
			"serverKey" : "uOdH8Jp7MTkMgsi45w5MkI20u+yOs="
		}
	},
	"roles" : [
		{
			"role" : "root",
			"db" : "admin"
		}
	]
}
</pre>

---
title: Autenticación  

Hasta la version 2.6 mongodb usaba autenticacion basada en un encriptamiento propio llamado mongo credentials.

<pre class="prettyprint" data-lang="json">
{
	"_id" : "admin.usr_admin_mdb",
	"user" : "usr_admin_mdb",
	"db" : "admin",
	"credentials" : {
<b>		"MONGODB-CR" : "2f6d476968bb3aca98e4336a936d5520"  </b>
	},
	"roles" : [
		{
			"role" : "root",
			"db" : "admin"
		}
	]
}



</pre>

---
title: Compresion de Indices
subtitle: storage.wiredTiger.indexConfig.prefixCompression

- Donde se guardan los indices de mongodb? 
- En RAM
- Si los indices se comprimen que estamos ahorrando?
- Obviamente RAM

<footer class="source"> https://docs.mongodb.org/v3.0/reference/configuration-options/#storage.wiredTiger.indexConfig.prefixCompression </footer>

---
title: YAML is better
subtitle: Nuevo archivo de configuracion.

Antes
<pre class="prettyprint" data-lang="bash">
storageEngine=wiredTiger
logpath=/var/log/mongodb/mongod.log
logappend=true
fork=true
port=27017
dbpath=/var/lib/mongo/
pidfilepath=/var/run/mongodb/mongod.pid
bindip=127.0.0.1
nojournal=true
cpu=true
</pre>
---
title: YAML is better
subtitle: Nuevo archivo de configuracion.

Despues
<pre class="prettyprint" data-lang="yaml">
systemLog:
   destination: file
   path: "/var/log/mongodb/mongod.log"
   logAppend: true
storage:
   wiredTiger:
      engineConfig:
         cacheSizeGB: <number>
      collectionConfig:
         blockCompressor: <string>
      indexConfig:
         prefixCompression: <boolean>
</pre>
---
title: Compatibilidad
subtitle: PHP Driver

<img height=300 src=figures/php1.png />

<footer class="source"> http://docs.mongodb.org/ecosystem/drivers/driver-compatibility-reference/ </footer>

---
title: Compatibilidad
subtitle: PHP Lenguaje

<img height=300 src=figures/php2.png />

<footer class="source"> http://docs.mongodb.org/ecosystem/drivers/driver-compatibility-reference/ </footer>

---
title: Compatibilidad
subtitle: NET/C# Driver

<img height=300 src=figures/net1.png />

<footer class="source"> http://docs.mongodb.org/ecosystem/drivers/driver-compatibility-reference/ </footer>

---
title: Compatibilidad
subtitle: NET/C# Lenguaje

<img height=300 src=figures/net2.png />

<footer class="source"> http://docs.mongodb.org/ecosystem/drivers/driver-compatibility-reference/ </footer>

---
title: MongoDB University
subtitle: Cursos para todos. 

<img height=450 src=figures/univ.png />

<footer class="source"> http://university.mongodb.org </footer>

