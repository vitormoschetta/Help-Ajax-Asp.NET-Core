# Ajax em Asp.NET Core

#### Usando a biblioteca Axios:

```
<script src="https://cdn.jsdelivr.net/npm/axios/dist/axios.min.js"></script>
<script>
  function AjaxAxios() {
        var url = '@Url.Action("RetornaDados","RequisicaoAjax")';
        axios.get(url)
            .then(function(response) {       
                console.log(response.data);
                document.getElementById('bloco-dados').innerHTML = response.data;                
            })
            .catch(function(error) {
                alert("Erro interno.");
            });   
  }
</script>
```


#### Usando jQuery:

###### Sem parâmetro:

```
<script>

    function AjaxJQuery() {
        var url = '@Url.Action("RetornaDados","RequisicaoAjax")';
        $.get(url, function (data) {
            console.log(data);
            $("#bloco-dados").empty();
            $("#bloco-dados").html(data);            
        })
        .fail(function(){
            alert("Erro interno");
        })
    }
</script>
```

###### Com parametro:

```
<script>

    function AjaxJQuery(value) {
        var url = '@Url.Action("RetornaDados","RequisicaoAjax")';
        $.get(url, {id: value}, function (data) {
            console.log(data);
            $("#bloco-dados").html(data);            
        })
        .fail(function(){
            alert("Erro interno");
        })
    }
</script>
```


#### Usando JS PURO / Vanilla JS
```
<script>

    function AjaxVanillaJS() {
        var url = '@Url.Action("RetornaDados","RequisicaoAjax")';
        var xhr = new XMLHttpRequest();
        xhr.open('GET', url);
        xhr.send(null);

        xhr.onreadystatechange = function() {
            if (xhr.readyState === 4) {
                if (xhr.status === 200) {
                    console.log(xhr.response);
                    document.getElementById('bloco-dados').innerHTML = xhr.response;                
                }
                else {
                    alert('Erro interno');
                }                
            }            
        }
    }
</script>
```


   
