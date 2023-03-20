### TR ###
 
 Eğer çıkan sonuçları sadece terminalde değil ".txt" olarak bilgisayarınızda da saklamak isterseniz kodu şu şekilde değiştirin;


    import requests

    from bs4 import BeautifulSoup

    url = "https://www.imdb.com/search/keyword/?keywords=anime"

    response = requests.get(url)
    html_icerigi = response.content

    soup = BeautifulSoup(html_icerigi,"html.parser")

    basliklar = soup.find_all("h3",{"class":"lister-item-header"})
    begeniler = soup.find_all("div",{"class":"inline-block ratings-imdb-rating"})

    with open("C:/Users/Dosya Yolu..../dosya_adı.txt","w",encoding="utf-8") as file:
        for baslik,begeni in zip(basliklar,begeniler):
            baslik = baslik.text
            begeni = begeni.text
            baslik = baslik.strip()
            baslik = baslik.replace("\n","")
            begeni = begeni.strip()
            begeni = begeni.replace("\n","")
            file.write("Başlık :" + baslik + "\n" )
            file.write("Beğeni :" + begeni + "\n\n")

### ENG ###

If you want to save the results not only in the terminal but also as a ".txt" file on your computer, you can modify the code as follows:


    import requests

    from bs4 import BeautifulSoup

    url = "https://www.imdb.com/search/keyword/?keywords=anime"

    response = requests.get(url)
    html_content = response.content

    soup = BeautifulSoup(html_content, "html.parser")

    titles = soup.find_all("h3", {"class": "lister-item-header"})
    ratings = soup.find_all("div", {"class": "inline-block ratings-imdb-rating"})

    with open("C:/Users/File Path.../file_name.txt", "w", encoding="utf-8") as file:
            for title, rating in zip(titles, ratings):
                title = title.text
                rating = rating.text
                title = title.strip()
                title = title.replace("\n","")
                rating = rating.strip()
                rating = rating.replace("\n","")
                file.write("Title: " + title + "\n" )
                file.write("Rating: " + rating + "\n\n")




