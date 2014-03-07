peliculas
=========
#!/usr/bin/env python
#
# Copyright 2007 Google Inc.
#
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtain a copy of the License at
#
#     http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.
#
import webapp2

class MainHandler(webapp2.RequestHandler):
    def get(self):
        self.response.write('Hello world!')

app = webapp2.WSGIApplication([
    ('/', MainHandler)
], debug=True)

import webapp2
import jinja2
import os

class MainHandler (webapp2.RequestHandler):
    def get (self):
        self.response.write('Hello word!')

app = webapp2.WSGIApplication([
    ('/', MainHandler)
], debug=True)

    directorio_plantillas = os.path.join(os.path.dirname(__file__), 'vista')
    entorno_jinja = jinja2.Environment(
        loader = jinja2.FileSystemLoader(directorio_plantillas),
        autoescape = True)

    def render_str(plantilla, **params):
        p = entorno_jinja.get_template(plantilla)
        return p.render(params)

    class Handler(webapp2.RequestHandler):
        def render(self, plantilla, **kw):
            self.response.out.write(render_str(plantilla, **kw))

        def write (self, *a, *kw):
            self.response.out.write(*a, **kw)

import webapp2
import jinja2
import os

class MainHandler(Handler):
    def get(self):
        self.render('index.html')


app = webapp2.WSGIApplication([
    ('/', MainHandler)
], debug=True)

    <!DOCTYPE html>
    <html lang="es">
        <head>
            <title> HOLA MUNDO </title>
        </head>
        <body>
            JELOU MUNDO!
        </body>
    <html>

import webapp2
import jinja2
import os

directorio_plantillas = os.path.join(os.path.dirname(__file__), 'vista')
entorno_jinja = jinja2.Environment(loader = jinja2.FileSystemLoader(directorio_plantillas), autoescape = True)

class Handler(webapp2.RequestHandler):
    def render(self, plantilla, **kw):
        self.reponse.out.write(render_str(plantilla, **kw))

    def write(self, *a, *kw):
        self.response.out.write(*a, **kw)

class MainHandler(Handler):
    def get(self):
        self.render('index.html')

app = webapp2.WSGIApplication([
    ('/', MainHandler)
], debug=True)


app = webapp2.WSGIApplication([
    ('/', MainHandler),
    ('/pagina1', ControladorParaPagina1),
    ('/pagina2', ControladorParaPagina2),
    ('/pagina3', ControladorParaPagina3)
], debug=True)

class ControladorParaPagina1(Handler):
    def get(self):
        self.render('PaginaHTML1.html')

class ControladorParaPagina2(Handler):
    def get(self):
    	self.render('PaginaHTML2.html')

class ControladorParaPagina3(Handler):
    def get(self):
    	self.render('PaginaHTML3.html')

class ControladorParaPagina1(Handler):
    def get(self):
    	libros = [{'nombre': 'Harry Potter','Fecha': '2012'},{'nombre': 'Los Juegos del Hambre','Fecha': '2013'}]
        self.render('PaginaHTML1.html', contenido = libros)


    <!DOCTYPE html>
    <html lang="es">
        <head>
            <title>Hola mundo</title>
        </head>
        <body>
            <h1>Lista de peliculas</h1>
            <ul>
            {% for libro in libros %}
                <li>
                    {{libro.nombre}} ({{libro.Fecha}})
                <li>
            {% endfor %}
            <ul>
        </body>
        
    <html>


