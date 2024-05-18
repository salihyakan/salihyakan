<h1 align="center">Hi 👋, I'm Salih Yakan</h1>
<p align="left"> <img src="https://komarev.com/ghpvc/?username=salihyakan&label=Profile%20views&color=0e75b6&style=flat" alt="salihyakan" /> </p>

<p align="left"> <a href="https://github.com/ryo-ma/github-profile-trophy"><img src="https://github-profile-trophy.vercel.app/?username=salihyakan&theme=" alt="salihyakan" /></a> </p>


- 📫 How to reach me **salihyakann@gmail.com**

<div> <a href="https://github.com/salihyakan" target="_blank"><img src="https://img.shields.io/badge/GitHub-100000?style=for-the-badge&logo=github&logoColor=white" target="_blank"></a>
<a href = "mailto:salihyakann@gmail.com"><img src="https://img.shields.io/badge/-Gmail-%23333?style=for-the-badge&logo=gmail&logoColor=white" target="_blank"></a>
</div><h3 align="left">Languages and Tools:</h3>
<p align="left">
<img src="https://raw.githubusercontent.com/teamedwardforever/Readme-Generator/71f25dd8b98329b168142a6b782a107b75eab178/svg/Skills/Languages/python-original.svg" alt="Python" width="40" height="40"/>
<img src="https://raw.githubusercontent.com/teamedwardforever/Readme-Generator/71f25dd8b98329b168142a6b782a107b75eab178/svg/Skills/Frontend/css3-original-wordmark.svg" alt="Css" width="40" height="40"/>
<img src="https://raw.githubusercontent.com/teamedwardforever/Readme-Generator/71f25dd8b98329b168142a6b782a107b75eab178/svg/Skills/Database/sqlite-icon.svg" alt="Sqlite" width="40" height="40"/>
<img src="https://raw.githubusercontent.com/teamedwardforever/Readme-Generator/71f25dd8b98329b168142a6b782a107b75eab178/svg/Skills/Database/postgresql-original-wordmark.svg" alt="Postgresql" width="40" height="40"/>
<img src="https://raw.githubusercontent.com/teamedwardforever/Readme-Generator/71f25dd8b98329b168142a6b782a107b75eab178/svg/Skills/Framework/django.svg" alt="Django" width="40" height="40"/>
<img src="https://raw.githubusercontent.com/teamedwardforever/Readme-Generator/71f25dd8b98329b168142a6b782a107b75eab178/svg/Skills/Software/getpostman-icon.svg" alt="Postman" width="40" height="40"/>
</p>

<h3 align="left">Stars</h3>
<img align="left" height="180em" src="https://github-readme-stats.vercel.app/api/top-langs/?username=salihyakan&layout=compact&theme=dark" alt=salihyakan />

<p>&nbsp;<img align="center" height="180em" src="https://github-readme-stats.vercel.app/api?username=salihyakan&show_icons=true&locale=en&theme=dark" alt="salihyakan" /></p>

<p><img align="center" height="180em" src="https://github-readme-streak-stats.herokuapp.com/?user=salihyakan&theme=dark" alt="salihyakan" /></p>

<img src="https://user-images.githubusercontent.com/73097560/115834477-dbab4500-a447-11eb-908a-139a6edaec5c.gif"><h2 align="left">⚡Activity Graph:</h2>
<img align="center" src="https://github-readme-activity-graph.vercel.app/graph?username=salihyakan&theme=react-dark"/>


name: generate animation

on:
  # run automatically every 24 hours
  schedule:
    - cron: "0 */24 * * *" 
  
  # allows to manually run the job at any time
  workflow_dispatch:
  
  # run on every push on the master branch
  push:
    branches:
    - master
    
  

jobs:
  generate:
    permissions: 
      contents: write
    runs-on: ubuntu-latest
    timeout-minutes: 5
    
    steps:
      # generates a snake game from a github user (<github_user_name>) contributions graph, output a svg animation at <svg_out_path>
      - name: generate github-contribution-grid-snake.svg
        uses: salihyakan/snk/svg-only@v3
        with:
          github_user_name: ${{ github.repository_owner }}
          outputs: |
            dist/github-contribution-grid-snake.svg
            dist/github-contribution-grid-snake-dark.svg?palette=github-dark
          
          
      # push the content of <build_dir> to a branch
      # the content will be available at https://raw.githubusercontent.com/<github_user>/<repository>/<target_branch>/<file> , or as github page
      - name: push github-contribution-grid-snake.svg to the output branch
        uses: crazy-max/ghaction-github-pages@v3.1.0
        with:
          target_branch: output
          build_dir: dist
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}