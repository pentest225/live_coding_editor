# live_coding_editor
créations des modèles de la plateforme de live coing 

## CREATION DES MODELS 

### TABLE module 
>Qui contiendras les differante module de notre plateforme 
>Leurs descriptions et autres 

### TABLE semaines
>Qui contidras les differentes sections de notre module 

### TABLE test  
>Cette table contiendras nos different quiz regroupe par semaine  

### TABLE questions 
>la table qui contiendras les differente questions par test . 


### TABLE response 
>la table qui contiendras differente reponse de l'utilisateur  .

### Table resultat 
>cette table nous servirra au classement des different user en fonctions de leurs resultats

## Table **Module**

```bash
   class Module(models.Model):
       titre = models.CharField(max_length=255)
       description = models.TextField()
```

## Table **Semaines**

```bash
   class Semaines(models.Model):
      module_id=models.ForeignKey(models,on_delete=models.CASCADE,related_name='Module_semaines')
      titre=models.CharField(max_length=255)
      date_add=models.DateTimeField(auto_now_add=True)
      date_up=models.DateTimeField(auto_now_add=True)
      date_expiration=models.DateTimeField()
```

## Tabel **Test**
```bash
  class Test(models.Model):
      semaine_id=models.ForeignKey(Semaines,on_delete=models.CASCADE,related_name='Semaines_test')
      Titre= models.CharField(max_length=255)
      date_add = models.DateTimeField(auto_now_add=True)
      date_up = models.DateTimeField(auto_now_add=True)
      date_expiration = models.DateTimeField()
```

## Tabel **Questions**
```bash
  class Questions(models.Model):
    test_id= models.ForeignKey(Test,on_delete=models.CASCADE,related_name='Test_questions')
    question_test=models.TextField()
    point_question =models.DecimalField()
    question_status=models.BooleanField(default=False)
```
>ici le status de la questions serra modifier en fonctions des traiement dans la tables respons 

## Tabel **Response**
```bash
 class response(models.Model):
    user_id=models.ForeignKey(User,on_delete=models.CASCADE,related_name='User_response')
    id_question=models.ForeignKey(Questions,on_delete=models.CASCADE,related_name='Questions_response')
    response_text=models.TextField()
```
>ici id_user serra enregistre losque l'utilisateur valide la ou les question(s) 
>ses reponses et son id  serons donc enregistre dans la table responce . 

