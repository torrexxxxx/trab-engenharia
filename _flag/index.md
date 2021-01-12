<!doctype html>
<html class="no-js" lang="">
<head>
  <meta charset="utf-8">
  <meta http-equiv="x-ua-compatible" content="ie=edge">
  <title>What the Flag?</title>
  <meta name="description" content="">
  <meta name="viewport" content="width=device-width, initial-scale=1, shrink-to-fit=no">
  <link rel="manifest" href="site.webmanifest">
  <link rel="apple-touch-icon" href="icon.png">
  <link rel="stylesheet" href="css/reset.css">
  <link rel="stylesheet" href="css/main.css">
  <link rel="stylesheet" type="text/css" href="font/material-icons.css"> 
</head>
<body>
  <section class="inicio">
    <h1>qum eh o cantor?</h1>    
    <button>INICIAR</button>
  </section> <!-- end .inicio -->

  <section class="flag flag-1">  
    <header>
      <p>
        <span class="mticons">star</span> 
        ACERTOS: <span class="acertos">0</span>
        
      </p>
      <p>
        <span class="mticons">alarm</span> 
        00:<span class="tempo">00</span>
      </p>
    </header>


    <div>
      <h1>O IDIOMA É O INGLÊS</h1>
      <ul>
        <li><img class="errado" src="img/img 9.jpg"></li>
        <li><img class="errado" src="img/img 7.jpg" id="ajuda"></li>
        <li><img class="errado" src="img/img 3.jpg"></li>
        <li><img class="errado" src="img/img 4.jpg"></li>
        <li><img class="certo" src="img/img 1.jpg" ></li>
        <li><img class="errado" src="img/img 6.jpg"></li>
        <li><img class="certo" src="img/img 2.jpg"></li>
        <li><img class="errado" src="img/img 8.jpg" id="ajuda2"></li>
        <li><img class="certo" src="img/img 5.jpg"></li>
      </ul>
    </div>

    <footer>
      <p>
        <span class="mticons home">home </span>
        <span class="mticons som">volume_up</span><!-- volume_off  -->
        <span class="mticons ajuda">help_outline</span>
      </p>
    </footer>
  </section><!-- end .flg  .flag-1  -->
 

  <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.4.1/jquery.min.js"></script>
  <script type="text/javascript"> 

$("section.inicio button").on("click", function() {
      musica01 = new Audio('musica/engenheiros.mp3');
      musica01.play();
      musica02 = new Audio('musica/artpopular.mp3');
      musica02.play();
      musica03 = new Audio('musica/capitalinicial.mp3');
      musica03.play();
  // Transição de Tela //
  $("section").hide();
  $("section.flag-1").show();

  setInterval(function(){
      var tempo = parseInt($("span.tempo").text());
      var soma = tempo + 1;
      if(soma < 10){
        soma = "0"+ soma;
      }
      $("span.tempo").text(soma);
    }, 1000);
  });

  $("section.flag-1 ul img.certo").one("click",function(){
    var acertos = parseInt($("span.acertos").text());
    var soma = acertos + 1;
    $("span.acertos").text(soma);
    $(this).css({opacity:0.5});

    if (soma == 3) { 
      musica01.pause();
      musica02.pause();
      musica03.pause();

    $("section").hide();
    $("section.flag-3").show();
    }
  });

  var erros = 0;
  $("section.flag-1 ul img.errado").one("click",function(){
    erros = erros + 1;
    $(this).css({opacity:0.5});
    
    if(erros > 1){
      musica01.pause();
      musica03.pause();
      musica02.pause(); 
      musica = new Audio('musica/game-over-acarde.wav');
      musica.play();
      // Transição de Tela //
      $("section").hide();
      $("section.flag-2").show();
    }
  });
  // botão home//
  $("section.flag-1 footer span.home").on("click",function(){
    musica.pause();
    $("section").hide();
    $("section.inicio").show();
  });
  
  // contador para o pause e despause da musica//
  var cont = 1;

  //pause e despause(vulgo play) da musica//
  $("section.flag-1 footer span.som").on("click",function(){
    if(cont == 1){
      musica01.pause();
      musica02.pause();
      musica03.pause();
      cont += 1;
    }
    else{
      musica.play();
      cont -=1; 
    }
  });

  //ajuda//
  $("section.flag-1 footer span.ajuda").on("click",function(){   
      $("#ajuda").hide();
      $("#ajuda2").hide();
  }); 

  </script>
  <script src="js/plugins.js"></script>
  <script src="js/main.js"></script>

  <section class="flag-2">
    <h1>Você Perdeu!!!</h1>    
  </section>

  <section class="flag-3">
    <h1>Você Ganhou!!!</h1>    
  </section>

</body>
</html>
